# Knowledge Modeling Quick Guide

*Created: 2025-02-27T08:45:00Z*  
*Last Modified: 2025-02-27T08:45:00Z*  
*Version: 1.0*

## Purpose

This guide provides practical patterns for modeling knowledge within the AI Capability Framework. It focuses on entity and relationship modeling to create effective knowledge structures that enhance AI assistance capabilities.

## Core Principles

1. **Entity-Relationship Structure** - Model knowledge as entities connected by meaningful relationships
2. **Descriptive Observations** - Attach clear, factual observations to entities
3. **Type Consistency** - Use consistent entity and relationship types
4. **Active Voice** - Express relationships in active voice for clarity
5. **Temporal Awareness** - Track knowledge creation and evolution over time

## Entity Modeling Patterns

### Entity Creation Best Practices

```
create_entities({
  entities: [
    {
      name: "Entity Name",         // Clear, specific identifier
      entityType: "Core Type",     // Consistent categorization
      observations: [              // Factual descriptions
        "Specific fact about entity",
        "Another relevant observation",
        "Important attribute or characteristic"
      ]
    }
  ]
})
```

### Effective Entity Naming

| Entity Type | Naming Pattern | Examples |
|-------------|----------------|----------|
| Concept | Noun or noun phrase | Machine Learning, Data Integrity |
| Person | Full name or role | John Smith, Project Manager |
| Organization | Official name | Acme Corporation, Research Team |
| Project | Descriptive title | AI Capability Framework, Data Pipeline |
| Process | Action-oriented phrase | Data Preprocessing, User Authentication |

### Entity Type Selection

Choose the most specific applicable type from this hierarchy:

1. **Concept** - Abstract ideas, theories, or mental constructs
2. **Person** - Individual human beings
3. **Organization** - Formal or informal groups of people
4. **Resource** - Physical or digital assets
5. **Process** - Sequences of actions or operations
6. **Event** - Occurrences at specific points in time
7. **Location** - Physical or virtual places
8. **Project** - Organized initiatives with specific goals
9. **Document** - Formalized information containers

### Observation Quality Guidelines

Effective observations are:
- **Specific** rather than general
- **Factual** rather than subjective
- **Concise** but comprehensive
- **Relevant** to the entity's role in the knowledge graph
- **Timestamped** where temporal context matters

## Relationship Modeling Patterns

### Relationship Creation Best Practices

```
create_relations({
  relations: [
    {
      from: "Source Entity",          // Entity where relation starts
      relationType: "active_verb",    // Clear relationship type
      to: "Target Entity"             // Entity where relation ends
    }
  ]
})
```

### Common Relationship Types

| Relationship Type | Usage | Example |
|-------------------|-------|---------|
| contains | Compositional relationship | Project contains Task |
| created_by | Authorship or creation | Document created_by Author |
| depends_on | Dependency relationship | Feature depends_on Infrastructure |
| implements | Realization relationship | Code implements Algorithm |
| part_of | Membership relationship | Module part_of System |
| precedes | Temporal sequence | Planning precedes Implementation |
| related_to | General association | Topic related_to Concept |
| uses | Utilization relationship | System uses Framework |

### Relationship Direction Guidelines

- Always use active voice from source to target
- Choose direction that most naturally expresses relationship
- Use inverse relationship pairs when bidirectional connections are important
- Consider whether A→B or B→A is more fundamental to domain understanding

### Temporal Relationship Considerations

- Use precedes/follows for sequential relationships
- Indicate when relationships began with timestamps when relevant
- Update relationships when they change rather than creating duplicates
- Use version numbers or dates to track relationship evolution

## Knowledge Integration Patterns

### Sequential Thinking Integration

```
// Using Knowledge Graph to inform Sequential Thinking
read_graph() -> sequential_thinking() -> add_observations()

// Example
let graph = read_graph();
let relevant_entities = graph.entities.filter(e => e.entityType === "Requirement");
let thought = `Based on ${relevant_entities.length} requirements, we should...`;
```

### Analysis Framework Integration

```
// Entity-based analysis structure
<understand>
  ${relevant_entities.map(e => e.observations.join("\n")).join("\n")}
</understand>

<analyze>
  ${graph.relations.filter(r => r.relationType === "affects").map(r => 
    `${r.from} affects ${r.to} in the following ways...`).join("\n")
  }
</analyze>
```

## Knowledge Modeling Examples

### Project Context Example

```javascript
// Create project and stakeholder entities
create_entities({
  entities: [
    {
      name: "Data Migration Project",
      entityType: "Project",
      observations: [
        "Project to migrate customer data to new CRM system",
        "Timeline: Q2 2025",
        "Critical priority due to legacy system EOL"
      ]
    },
    {
      name: "IT Department",
      entityType: "Organization",
      observations: [
        "Responsible for technical implementation",
        "Has experience with similar migrations",
        "Limited resources due to parallel projects"
      ]
    }
  ]
});

// Create relationships
create_relations({
  relations: [
    {
      from: "IT Department",
      relationType: "manages",
      to: "Data Migration Project"
    },
    {
      from: "Data Migration Project",
      relationType: "depends_on",
      to: "Legacy System API"
    }
  ]
});
```

### Technical System Example

```javascript
// Create system component entities
create_entities({
  entities: [
    {
      name: "Authentication Service",
      entityType: "Process",
      observations: [
        "Handles user authentication and authorization",
        "Implements OAuth 2.0 protocol",
        "Maintains session state in Redis"
      ]
    },
    {
      name: "User Database",
      entityType: "Resource",
      observations: [
        "PostgreSQL database storing user profiles",
        "Contains sensitive personal information",
        "Encrypted at rest and in transit"
      ]
    }
  ]
});

// Create technical relationships
create_relations({
  relations: [
    {
      from: "Authentication Service",
      relationType: "reads_from",
      to: "User Database"
    },
    {
      from: "Authentication Service",
      relationType: "implements",
      to: "Security Protocol"
    }
  ]
});
```

## Implementation Notes

This guide provides general patterns that should be adapted to specific domains and requirements. Consistency is more important than strict adherence to these guidelines. As the knowledge graph grows, periodically review for consistency and optimize for the most frequent query patterns.
