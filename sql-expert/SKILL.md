---
name: sql-expert
description: >
  Write, optimize, and debug SQL queries. Use when user shares SQL that s wrong or slow,
  asks "write a SQL query for X", "optimize this query", "why is this slow", "how do I join
  these tables", or needs help with database schema, indexes, or migrations.
---
# SQL Expert

## JOIN Types
INNER JOIN - only matching rows
LEFT JOIN  - all left + matching right
RIGHT JOIN - all right + matching left
FULL JOIN  - all rows from both

## Optimization Checklist
1. Index on WHERE, JOIN, ORDER BY columns
2. Avoid functions on indexed columns in WHERE
3. EXPLAIN ANALYZE to check query plan
4. Avoid N+1 - use JOINs not loops
5. LIMIT results when possible

## Common Patterns
-- Upsert (PostgreSQL)
INSERT INTO users (email, name) VALUES (?, ?)
ON CONFLICT (email) DO UPDATE SET name = EXCLUDED.name;

-- Soft delete
UPDATE records SET deleted_at = NOW() WHERE id = ?;
SELECT * FROM records WHERE deleted_at IS NULL;

-- Pagination
SELECT * FROM listings ORDER BY created_at DESC LIMIT 20 OFFSET 40;

-- Window function
SELECT agent, sales, RANK() OVER (PARTITION BY suburb ORDER BY sales DESC) as rank FROM stats;

Provide: working SQL + explanation + index recommendations
