# Football Ticket Booking System — Database Design & SQL Queries

A simplified relational database for a football ticket booking platform, built for the Apollo Level 2 Web Dev program (Assignment B7A3). Covers ERD design, primary/foreign keys, and SQL queries using joins, subqueries, aggregation, pattern matching, null handling, and pagination.

## Project overview

The system tracks three things:

- **Users** — football fans and ticket managers who use the platform
- **Matches** — upcoming tournament fixtures and their base ticket pricing
- **Bookings** — individual ticket purchases linking a user to a match

## Entity relationship diagram

🔗 **ERD link:** https://drive.google.com/file/d/1TtF-Z2fj4ASeE9tTJe3CoEGdMkysWxmI/view?usp=sharing

| Relationship | Type |
|---|---|
| Users → Bookings | One-to-Many |
| Matches → Bookings | Many-to-One |
| One Bookings row | One user + one match for one reserved seat |

## Database schema

**Users**

| Field | Description |
|---|---|
| `user_id` (PK) | Unique user identifier |
| `full_name` | First and last name |
| `email` | Login email |
| `role` | `Ticket Manager` or `Football Fan` |
| `phone_number` | Contact number |

**Matches**

| Field | Description |
|---|---|
| `match_id` (PK) | Unique match identifier |
| `fixture` | Competing teams |
| `tournament_category` | League/cup name |
| `base_ticket_price` | Standard seat price |
| `match_status` | `Available`, `Selling Fast`, `Sold Out`, `Postponed` |

**Bookings**

| Field | Description |
|---|---|
| `booking_id` (PK) | Unique booking/transaction id |
| `user_id` (FK → Users) | Who made the booking |
| `match_id` (FK → Matches) | Which match it's for |
| `seat_number` | Allocated seat (e.g. `A-12`) |
| `payment_status` | `Pending`, `Confirmed`, `Cancelled`, `Refunded` |
| `total_cost` | Final invoice price |

## Files in this repo

| File | Contents |
|---|---|
| `QUERY.sql` | Table creation, sample data, and all 7 assignment queries |
| `README.md` | Project documentation (this file) |

## SQL queries

1. Champions League matches that are currently `Available`
2. Users named `Tanvir...` or whose name contains `Haque`
3. Bookings with a missing payment status, shown as `Action Required`
4. Booking details joined with the fan's name and the match fixture
5. All users with their booking ids, including fans who never booked
6. Bookings priced strictly above the average booking cost
7. The 2nd and 3rd most expensive matches (pagination)

## How to run

```bash
createdb football_ticket_db
psql -d football_ticket_db -f QUERY.sql
```

## Concepts demonstrated

`JOIN` variants (`INNER`, `LEFT`) · subqueries · aggregation (`AVG`) · pattern matching (`LIKE` / `ILIKE`) · null handling (`COALESCE`, `IS NULL`) · pagination (`LIMIT` / `OFFSET`)

## Additional submission links

- 🎤 Viva video walkthrough:
- https://drive.google.com/file/d/126Nw4nQWpLue7rAj6T6AByrhzyHWn7Gf/view?usp=sharing
- https://drive.google.com/file/d/1qY5UCRjnFnSlfzwgUuyMmtjBvX_8GgXC/view?usp=sharing
- https://drive.google.com/file/d/1tvCKuQ7mD33SFlTNJ5pk3BdV_10D8g9G/view?usp=sharing

## Author

**Muntacir Tamim** ([@Muntacir-Tamim](https://github.com/Muntacir-Tamim))
