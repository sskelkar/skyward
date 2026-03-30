# Multi-Service Architecture Guide
## Building 2-3 Services with Agent Teams

This guide explains how directors should structure their departments as multiple microservices, each built by dedicated agent teams.

---

## Core Concept

**Instead of building one monolithic system, you build 2-3 focused services:**
- Each service has a clear responsibility
- Each service is built by a dedicated agent team (1-3 agents)
- Services can call each other locally
- All services run on your laptop

---

## Example Architectures by Role

### Director of Booking Portal

**Service 1: Search API (Backend)**
- Agent Team: 1-2 backend agents
- Responsibility: Flight search, filtering, sorting
- Runs on: `http://localhost:5001`
- Tech: Flask/FastAPI
- Demo: Query flights, show JSON results

**Service 2: Booking API (Backend)**
- Agent Team: 1-2 backend agents
- Responsibility: Create bookings, payments, confirmations
- Runs on: `http://localhost:5002`
- Tech: Flask/FastAPI
- Demo: Create booking, show confirmation

**Service 3: Web Frontend (UI)**
- Agent Team: 1-2 frontend agents
- Responsibility: User interface, booking flow
- Runs on: `http://localhost:3000`
- Tech: React/Vue/vanilla JS
- Demo: Visual booking experience

---

### Director of Inventory

**Service 1: Flight Management API**
- Agent Team: Backend agents
- Responsibility: CRUD operations for flights
- Runs on: `http://localhost:5010`
- Demo: Admin creates/edits flights

**Service 2: Seat Inventory API**
- Agent Team: Backend agents
- Responsibility: Seat tracking, availability
- Runs on: `http://localhost:5011`
- Demo: Real-time seat availability

**Service 3: Admin Dashboard**
- Agent Team: Frontend agents
- Responsibility: Visual inventory management
- Runs on: `http://localhost:3010`
- Demo: Dashboard showing inventory status

---

### Director of Check-in

**Service 1: Check-in API**
- Agent Team: Backend agents
- Responsibility: Check-in logic, validation
- Runs on: `http://localhost:5020`
- Demo: Check-in processing

**Service 2: Seat Assignment Service**
- Agent Team: Algorithm agents
- Responsibility: Seat selection, optimization
- Runs on: `http://localhost:5021`
- Demo: Automatic seat assignment

**Service 3: Boarding Pass Generator**
- Agent Team: Frontend + backend agents
- Responsibility: Generate passes, QR codes
- Runs on: `http://localhost:3020`
- Demo: Beautiful boarding pass with QR

---

## Multi-Agent Team Strategies

### Strategy 1: Sequential Service Building
**When:** Building 3 services in 30 minutes

```
Minutes 0-10: Agent Team A builds Service 1
Minutes 10-20: Agent Team B builds Service 2
Minutes 20-28: Agent Team C builds Service 3
Minutes 28-30: Test integration, prepare demo
```

**Example prompts:**
```
Agent Team A (Service 1):
"Build a Flask API for flight search:
- GET /api/flights?origin=X&dest=Y
- Return mock flight data
- Run on port 5001"

[Wait for completion]

Agent Team B (Service 2):
"Build a Flask API for bookings:
- POST /api/bookings
- Uses data from http://localhost:5001
- Run on port 5002"

[Wait for completion]

Agent Team C (Service 3):
"Build a simple web UI:
- Calls http://localhost:5001 for search
- Calls http://localhost:5002 for booking
- Serve on port 3000"
```

---

### Strategy 2: Parallel Service Building
**When:** Services are independent

```
Start 3 agent teams simultaneously:

Agent Team A: "Build Service 1..."
Agent Team B: "Build Service 2..."
Agent Team C: "Build Service 3..."

[All work in parallel for 20 minutes]

Minutes 20-28: Integration agent connects them
Minutes 28-30: Test and demo
```

---

### Strategy 3: Iterative Service Enhancement
**When:** Starting simple, adding complexity

**Q1:** Build 1 simple service with 1 agent team
**Q2:** Add 2nd service, integrate
**Q3:** Add 3rd service, enhance all
**Q4:** Polish and optimize all services

---

## Local Development Setup

### Option A: Simple Terminal Windows

```bash
# Terminal 1
cd service-1
python app.py  # Runs on port 5001

# Terminal 2
cd service-2
python app.py  # Runs on port 5002

# Terminal 3
cd service-3
npm start  # Runs on port 3000
```

**Pros:** Simple, no setup
**Cons:** Manual management

---

### Option B: Docker Compose

**docker-compose.yml:**
```yaml
version: '3.8'
services:
  search-api:
    build: ./search-service
    ports:
      - "5001:5000"
    volumes:
      - ./search-service:/app

  booking-api:
    build: ./booking-service
    ports:
      - "5002:5000"
    volumes:
      - ./booking-service:/app

  frontend:
    build: ./frontend
    ports:
      - "3000:3000"
    volumes:
      - ./frontend:/app
    depends_on:
      - search-api
      - booking-api
```

**Commands:**
```bash
docker-compose up  # Start all services
docker-compose down  # Stop all
docker-compose logs -f  # View logs
```

**Pros:**
- All services start together
- Consistent environment
- Easy networking

**Cons:**
- Requires Docker installed
- Slightly more setup

---

### Option C: Process Manager (PM2)

**ecosystem.config.js:**
```javascript
module.exports = {
  apps: [
    {
      name: 'search-api',
      script: 'service-1/app.py',
      interpreter: 'python3'
    },
    {
      name: 'booking-api',
      script: 'service-2/app.py',
      interpreter: 'python3'
    },
    {
      name: 'frontend',
      script: 'npm',
      args: 'start',
      cwd: './frontend'
    }
  ]
}
```

**Commands:**
```bash
pm2 start ecosystem.config.js
pm2 stop all
pm2 logs
```

---

## Service-to-Service Communication

### Within Your Laptop (Easy)

**Service 1 calls Service 2:**
```python
# In Service 1
import requests

def get_flight_data():
    response = requests.get('http://localhost:5002/api/flights')
    return response.json()
```

**Service 3 (Frontend) calls Services 1 & 2:**
```javascript
// In frontend
async function searchFlights() {
    const response = await fetch('http://localhost:5001/api/flights?origin=SFO');
    const flights = await response.json();
    return flights;
}

async function bookFlight(flightId) {
    const response = await fetch('http://localhost:5002/api/bookings', {
        method: 'POST',
        body: JSON.stringify({flight_id: flightId})
    });
    return response.json();
}
```

---

### Across Laptops (Advanced)

#### Option 1: ngrok (Easiest)
```bash
# On Director A's laptop
ngrok http 5001
# Get URL: https://abc123.ngrok.io

# Director B uses it
curl https://abc123.ngrok.io/api/flights
```

#### Option 2: Local Network
```bash
# Find your IP
ifconfig  # Look for 192.168.x.x

# Director A's service runs on 192.168.1.100:5001
# Director B calls: http://192.168.1.100:5001/api/flights
```

#### Option 3: Mock It
```python
# Instead of calling real service, mock the response
def get_inventory_data():
    # In real integration: return requests.get('http://other-laptop:5010/api/inventory').json()
    # For demo: return mock data
    return {
        "flight_id": "SK123",
        "seats_available": 42
    }
```

**Recommendation:** Use mocks for Q1-Q3, try real integration in Q4 if desired.

---

## Agent Team Coordination

### Pattern 1: Specialist Agent Teams

Assign permanent roles to agent teams:

**Agent Team A (Backend Specialists):**
- Builds Service 1 (Q1)
- Builds Service 2 (Q2)
- Maintains both services (Q3-Q4)

**Agent Team B (Frontend Specialists):**
- Builds Service 3 (Q2)
- Enhances UI (Q3-Q4)

**Agent Team C (Integration Specialists):**
- Connects services (Q3)
- Handles testing (Q4)

---

### Pattern 2: Service-Dedicated Teams

Each agent team owns one service permanently:

**Agent Team for Service 1:**
- Q1: Build initial version
- Q2: Add features
- Q3: Optimize
- Q4: Final polish

**Agent Team for Service 2:**
- Q1: Build initial version
- [etc.]

---

### Pattern 3: Dynamic Teams

Reorganize agents each quarter based on needs:

**Q1:** All agents focus on Service 1 (get it working)
**Q2:** Split - 2 agents on Service 2, 1 enhances Service 1
**Q3:** Add Service 3 with new agent team
**Q4:** All agents polish and integrate

---

## Demo Strategy

### Quarter 1: Show One Service
- Demo Service 1 working standalone
- "Here's the search API returning flight data"

### Quarter 2: Show Two Services
- Demo Service 1 + Service 2
- "Search API feeds into Booking API"

### Quarter 3: Show All Three Services
- Demo complete integrated system
- "Frontend calls Search API, then Booking API"

### Quarter 4: Show Polished System
- Demo end-to-end flow, all services
- "Full user journey across all services"

---

## Troubleshooting

### "Services can't talk to each other"
- Check ports (no conflicts?)
- Check URLs (http://localhost:5001 not http://5001)
- Try curl first to verify service is up
- Check CORS if frontend calling backend

### "Can't run multiple Python apps"
- Use different ports: one on 5001, one on 5002
- Use different virtual environments
- Or use Docker to isolate

### "Frontend can't call backend (CORS)"
```python
# In Flask
from flask_cors import CORS
app = Flask(__name__)
CORS(app)  # Enable CORS for all routes
```

### "Too complex, running out of time"
- Drop to 2 services instead of 3
- Make services simpler
- Use mocks instead of real integration
- Focus on one polished service > three broken ones

---

## Quick Start Checklist

**Before Quarter 1:**
- [ ] Decide: 2 or 3 services?
- [ ] Assign ports (avoid conflicts with others)
- [ ] Choose tech stack
- [ ] Decide: terminals, Docker, or PM2?

**During Each Quarter:**
- [ ] Start agent teams for each service
- [ ] Build services on assigned ports
- [ ] Test each service individually
- [ ] Test services calling each other
- [ ] Prepare integrated demo

**Demo Readiness:**
- [ ] All services running
- [ ] Can demonstrate flow across services
- [ ] Have backup plan (show services separately if integration breaks)

---

## Key Takeaways

1. **2-3 services is optimal** - More is cognitive overload
2. **Dedicated agent teams** - Each service has its own agents
3. **Local-first** - Everything on localhost, no cloud needed
4. **Mock when needed** - Don't let integration block progress
5. **Service boundaries** - Each service has clear responsibility
6. **Incremental demos** - Show progress service by service

**Remember:** The goal is learning multi-agent orchestration, not building production microservices. Keep it simple, keep it local, keep it working.

---

**Good luck building your department's services!** 🚀
