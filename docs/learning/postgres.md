# PostgreSQL Learning Notes

## What PostgreSQL is

PostgreSQL is a relational database. It stores structured data in tables, connects related rows with keys, and enforces rules such as required values and uniqueness.

## Concepts to learn

- **Table:** a collection of rows with defined columns.
- **Primary key:** a value that identifies a row.
- **Foreign key:** a constraint that links a row to another table.
- **Constraint:** a database rule, such as `NOT NULL`, `UNIQUE`, or a check on valid values.
- **Transaction:** a group of database operations that succeed or fail together.
- **Index:** a data structure that can speed up lookups, with a cost in storage and write time.

## FitCoach context

FitCoach plans to use Supabase-hosted PostgreSQL initially, with Prisma for schema and application data access. Workout sessions, exercise sets, meals, and nutrition entries will have relationships and integrity rules that belong in the database as well as application validation.

A local PostgreSQL container is not part of the current development setup. We can add one when local database development is useful; until then, Docker runs the Node.js and PNPM development tools.
