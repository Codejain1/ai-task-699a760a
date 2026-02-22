```json
{
  "status": "success",
  "result": {
    "optimization_recommendations": [
      {
        "category": "Indexing",
        "recommendations": [
          {
            "action": "Add composite indexes for frequently queried columns",
            "example": "CREATE INDEX idx_user_status_created ON users(status, created_at)",
            "impact": "High - Can reduce query time by 70-90%"
          },
          {
            "action": "Remove unused indexes to reduce write overhead",
            "example": "DROP INDEX idx_unused_column",
            "impact": "Medium - Improves INSERT/UPDATE performance"
          },
          {
            "action": "Use partial indexes for filtered queries",
            "example": "CREATE INDEX idx_active_users ON users(id) WHERE status = 'active'",
            "impact": "Medium - Reduces index size and improves performance"
          }
        ]
      },
      {
        "category": "Query Optimization",
        "recommendations": [
          {
            "action": "Rewrite N+1 queries using JOINs or batch loading",
            "example": "SELECT u.*, p.title FROM users u LEFT JOIN posts p ON u.id = p.user_id",
            "impact": "Very High - Can reduce queries from hundreds to single digits"
          },
          {
            "action": "Use LIMIT with proper pagination",
            "example": "SELECT * FROM table ORDER BY id LIMIT 20 OFFSET 0",
            "impact": "High - Prevents loading unnecessary data"
          },
          {
            "action": "Optimize WHERE clauses with proper column ordering",
            "example": "Use indexed columns first in WHERE conditions",
            "impact": "Medium - Improves index utilization"
          }
        ]
      },
      {
        "category": "Schema Optimization",
        "recommendations": [
          {
            "action": "Normalize database schema to reduce redundancy",
            "example": "Split large tables into related entities",
            "impact": "Medium - Reduces storage and improves consistency"
          },
          {
            "action": "Use appropriate data types",
            "example": "Use INT instead of VARCHAR for numeric IDs",
            "impact": "Medium - Reduces storage and improves comparison speed"
          },
          {
            "action": "Implement table partitioning for large datasets",
            "example": "PARTITION BY RANGE (created_date)",
            "impact": "High - Improves query performance on large tables"
          }
        ]
      },
      {
        "category": "Caching Strategy",
        "recommendations": [
          {
            "action": "Implement query result caching",
            "example": "Use Redis or Memcached for frequently accessed data",
            "impact": "Very High - Can reduce database load by 80%+"
          },
          {
            "action": "Cache database connection pools",
            "example": "Configure connection pooling with appropriate min/max connections",
            "impact": "Medium - Reduces connection overhead"
          }
        ]
      }
    ],
    "monitoring_setup": {
      "query_analysis": [
        "Enable slow query logging",
        "Monitor query execution plans",
        "Track database performance metrics",
        "Set up alerts for performance degradation"
      ],
      "tools": [
        "EXPLAIN ANALYZE for PostgreSQL",
        "MySQL Performance Schema",
        "Database monitoring dashboards",
        "APM tools for query tracing"
      ]
    },
    "implementation_priority": [
      {
        "priority": 1,
        "task": "Identify and fix N+1 queries",
        "effort": "Medium",
        "impact": "Very High"
      },
      {
        "priority": 2,
        "task": "Add missing indexes based on query patterns",
        "effort": "Low",
        "impact": "High"
      },
      {
        "priority": 3,
        "task": "Implement caching for frequently accessed data",
        "effort": "Medium",
        "impact": "Very High"
      },
      {
        "priority": 4,
        "task": "Optimize complex queries with better JOINs",
        "effort": "High",
        "impact": "High"
      },
      {
        "priority": 5,
        "task": "Review and optimize database schema",
        "effort": "High",
        "impact": "Medium"
      }
    ]
  },
  "summary": "Generated comprehensive database query performance optimization recommendations covering indexing strategies, query optimization techniques, schema improvements, caching implementation, and monitoring setup with prioritized action items.",
  "confidence": 92
}
```