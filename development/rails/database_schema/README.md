# Development - Rails - Database Schema

This document outlines best practices regarding Rails database migrations and
schema design.

## Column naming conventions

* `boolean` columns **must** have one of the prefixes `can_`, `is_` or `has_`
* `datetime/timestamp` columns **must** have the suffix `_at`
* `date` columns **must** have the suffix `_on`

## Foreign keys

When a foreign key on a non-polymorphic association is required, there **must**
be a foreign key constraint on the association.
