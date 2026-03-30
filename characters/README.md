# CHARACTER SHEETS

This directory contains detailed character sheets for all 8 director roles in Terminal Velocity.

## Available Roles

### Customer-Facing Departments

1. **[Director of Customer Booking Portal](booking-portal.md)**
   - Build the customer-facing flight booking application
   - Focus: Frontend, UX, conversion optimization
   - Best for: Engineers who enjoy UI/UX work
   - Visual demos: Search interfaces, booking flows, payment forms

2. **[Director of Customer Service & Support](customer-service.md)**
   - Build chatbots, ticketing, and support automation
   - Focus: AI/NLP, automation, customer satisfaction
   - Best for: Engineers interested in AI and automation
   - Visual demos: Chatbot conversations, support dashboards, ticket systems

### Data & Intelligence

3. **[Director of Pricing & Revenue Optimization](pricing-revenue.md)**
   - Build dynamic pricing and revenue analytics
   - Focus: Algorithms, analytics, business logic
   - Best for: Engineers who love data and optimization
   - Visual demos: Pricing dashboards, revenue charts, competitor analysis

4. **[Director of Personalization & Recommendations](recommendations.md)**
   - Build recommendation engines and personalization
   - Focus: ML, user segmentation, A/B testing
   - Best for: Engineers interested in ML and growth
   - Visual demos: Recommendation widgets, user dashboards, analytics

### Backend Operations

5. **[Director of Flight Inventory & Scheduling](inventory-scheduling.md)**
   - Build flight schedules and seat inventory tracking
   - Focus: Backend systems, databases, business logic
   - Best for: Classic backend engineers
   - Visual demos: Admin dashboards, inventory charts, schedule views

6. **[Director of Check-in & Boarding](checkin-boarding.md)**
   - Build check-in, seat selection, and boarding systems
   - Focus: Seat algorithms, QR codes, operations
   - Best for: Backend engineers who want some frontend
   - Visual demos: Seat maps, boarding passes, gate dashboards

7. **[Director of Flight Status & Tracking](flight-status.md)**
   - Build real-time flight tracking and status systems
   - Focus: Real-time data, maps, notifications
   - Best for: Engineers who love real-time systems
   - Visual demos: Flight maps, status boards, live updates

### Growth & Marketing

8. **[Director of Marketing & Growth](marketing-growth.md)**
   - Build marketing campaigns and growth analytics
   - Focus: A/B testing, attribution, campaign automation
   - Best for: Engineers interested in growth and experimentation
   - Visual demos: Campaign dashboards, landing pages, analytics

---

## How to Choose a Role

### By Interest
- **Love frontend?** → Booking Portal, Check-in & Boarding
- **Love backend?** → Inventory, Pricing, Flight Status
- **Love ML/AI?** → Recommendations, Customer Service
- **Love analytics?** → Pricing, Marketing, Recommendations
- **Love real-time systems?** → Flight Status, Customer Service

### By Complexity
- **Simpler:** Booking Portal, Check-in & Boarding, Marketing
- **Moderate:** Customer Service, Flight Status, Inventory
- **More Complex:** Pricing, Recommendations

### By Visual Impact
- **Most Visual:** Booking Portal, Check-in (seat maps), Flight Status (maps)
- **Dashboard-Heavy:** Pricing, Marketing, Inventory
- **AI/Chat-Heavy:** Customer Service, Recommendations

### Role Comparison Table

| Role | Frontend | Backend | ML/AI | Visual Impact | Complexity |
|------|----------|---------|-------|---------------|------------|
| Booking Portal | ⭐⭐⭐ | ⭐⭐ | ⭐ | ⭐⭐⭐ | Medium |
| Inventory | ⭐ | ⭐⭐⭐ | ⭐ | ⭐⭐ | Medium |
| Pricing | ⭐ | ⭐⭐ | ⭐⭐ | ⭐⭐ | High |
| Recommendations | ⭐ | ⭐⭐ | ⭐⭐⭐ | ⭐⭐ | High |
| Customer Service | ⭐ | ⭐⭐ | ⭐⭐⭐ | ⭐⭐ | Medium |
| Marketing | ⭐⭐ | ⭐⭐ | ⭐ | ⭐⭐ | Medium |
| Check-in & Boarding | ⭐⭐ | ⭐⭐⭐ | ⭐ | ⭐⭐⭐ | Medium |
| Flight Status | ⭐⭐ | ⭐⭐⭐ | ⭐ | ⭐⭐⭐ | Medium |

**Legend:**
- ⭐⭐⭐ = Primary focus / High
- ⭐⭐ = Secondary focus / Medium
- ⭐ = Minimal involvement / Low

---

## Character Sheet Structure

Each character sheet includes:

1. **Your North Star** - Your guiding principle and motivation
2. **What You'll Build** - Quarter-by-quarter build targets
3. **Visual Demo Examples** - What "good" looks like (Bronze/Silver/Gold)
4. **Multi-Agent Strategies** - 4 concrete strategies with example prompts
5. **Common Challenges & Solutions** - Practical troubleshooting
6. **Tech Stack Suggestions** - Recommended tools and frameworks
7. **Quarter-by-Quarter Goals** - Specific objectives for each turn
8. **Success Metrics** - How to know you're succeeding
9. **Character Flavor** - Personality, mantras, and style
10. **Quick Start Guide** - How to begin in the first 5 minutes

---

## Team Composition Suggestions

### For 4 Players
**Balanced:**
1. Booking Portal (frontend)
2. Inventory (backend)
3. Recommendations (ML)
4. Check-in (operations)

**Backend-Heavy:**
1. Inventory (core backend)
2. Pricing (analytics)
3. Flight Status (real-time)
4. Check-in (operations)

### For 5 Players
Add Marketing or Customer Service to any 4-player combination

### For 6 Players
**Full Coverage:**
1. Booking Portal
2. Inventory
3. Pricing
4. Recommendations
5. Customer Service
6. Check-in or Flight Status

---

## Role Dependencies (Minimal)

All roles work independently, but optional light integration:

- **Booking Portal** can call Inventory for availability, Pricing for prices
- **Recommendations** can use Inventory data, integrate with Booking Portal
- **Check-in** can use Inventory for seat status, Flight Status for updates
- **Flight Status** can notify Customer Service, Check-in
- **Marketing** can track conversions from Booking Portal

**Remember:** Integration is optional! Each role can work with mock data.

---

## Getting Started

1. **Read this README** to understand all roles
2. **Choose your role** based on interests and team composition
3. **Read your character sheet** thoroughly (15 minutes)
4. **Note the multi-agent strategies** - you'll use these
5. **Start Quarter 1** with the Quick Start Guide in your sheet

---

## Questions?

Each character sheet answers:
- What should I build? (What You'll Build section)
- How do I use agents? (Multi-Agent Strategies section)
- What if I get stuck? (Common Challenges section)
- How do I know if I'm succeeding? (Success Metrics section)

If you're still unsure, ask the gamerunner or pick a role that sounds fun - you can always adapt as you play!

---

**Good luck, Directors. Let's build an airline.** ✈️
