# Hospital Estimate Builder

A billing estimate calculator built for a hospital client, so front-desk and finance staff can put together an itemized cost estimate for a patient's stay before treatment begins, instead of working it out by hand.

## How it works

A user picks a patient category (Charity, General NC A/B, General, Deluxe, Super Deluxe), enters the expected length of stay, and selects the services the patient is expected to need across categories like nursing, room charges, doctor visits, laboratory, radiology, pharmacy, equipment, procedures, and surgery.

For each selected service, the app works out a line total:

- **One-time charges** (e.g. a lab test) are billed at the service's MRP once.
- **Daily charges** (e.g. room rent, nursing) are billed at MRP × visits-per-day × length of stay.

It then looks up whether a discount rule exists for that specific combination of patient category and service category. Discounts can be a flat amount per unit or a percentage of the line total, and are applied per line, not as a single blanket discount on the invoice. The estimate response returns each line's unit price, quantity, discount, and final amount, plus a summary with subtotal, total discount, and final total.

Estimates can be saved (numbered sequentially, e.g. EST001) and pulled back up later, with users seeing only their own saved estimates while managers and admins can see across users.

There are three roles with different levels of access:

- **User** — builds and saves estimates.
- **Manager** — same as a user, plus managing services and discount rules.
- **Admin** — full access, including approving/rejecting new signups and managing service and patient categories.

New accounts require admin approval before they can log in, except for the very first admin account created, which is auto-approved.

Admins and managers can also bulk-upload services and discount rules via CSV or Excel, using downloadable templates that match the expected columns.

## Tech stack

- **Backend:** Python, Flask, with Flask-Login for session-based auth and Flask-SQLAlchemy over SQLite for storage
- **Frontend:** Server-rendered Jinja templates with plain HTML/CSS and vanilla JavaScript (no frontend framework or build step)
- **Data import:** pandas for parsing bulk CSV/Excel uploads

---

**Ankit Singh**
[LinkedIn](https://www.linkedin.com/in/ankit-singh-117925249/)
