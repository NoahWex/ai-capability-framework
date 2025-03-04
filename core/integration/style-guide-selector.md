# Style Guide Selector

*Created: 2025-03-04*  
*Version: 1.0*

## Purpose

The Style Guide Selector helps users choose the most appropriate style guide or framework for their specific needs. This tool simplifies the decision-making process based on the problem type, desired outcomes, and work context.

## Quick Selection Guide

### Choose by Primary Goal

| If your goal is to... | Then use... | Key benefit |
|-----------------------|-------------|-------------|
| Analyze a complex problem | **Adaptive Analysis Framework** | Structured problem decomposition |
| Organize knowledge and relationships | **Knowledge Modeling Guide** | Clear entity-relationship mapping |
| Implement a specific feature or component | **TRACE Framework** | Explicit scope control and progressive development |

### Choose by Problem Type

#### Analysis-Oriented Problems

Use the **Adaptive Analysis Framework** when:
- Breaking down complex issues into components
- Evaluating multiple options or approaches
- Making structured decisions with clear criteria
- Planning implementation at a high level

Example indicators:
- "I need to analyze this problem"
- "Help me think through these options"
- "What's the best approach for this situation?"

#### Knowledge-Oriented Problems

Use the **Knowledge Modeling Guide** when:
- Mapping relationships between concepts or entities
- Organizing domain knowledge systematically
- Representing complex systems and their components
- Building knowledge graphs or ontologies

Example indicators:
- "Let's map out these relationships"
- "I need to organize this information clearly"
- "How do these components relate to each other?"

#### Implementation-Oriented Problems

Use the **TRACE Framework** when:
- Building a specific feature or component
- Requiring clear scope boundaries
- Developing solutions in progressive stages
- Focusing on practical implementation

Example indicators:
- "I need to implement this feature"
- "Let's build this component"
- "We need to be careful about scope"
- "Develop this in stages"

## Decision Tree

Start by asking: **What's the primary focus of your work?**

```
1. Understanding and analyzing a problem
   └── Is knowledge organization a key component?
       ├── YES → Consider hybrid approach with Knowledge Modeling + Analysis
       └── NO → Use Adaptive Analysis Framework
          
2. Organizing information and relationships
   └── Is implementation a key component?
       ├── YES → Consider hybrid approach with Knowledge Modeling + TRACE
       └── NO → Use Knowledge Modeling Guide
       
3. Implementing a specific solution
   └── Is complex analysis needed before implementation?
       ├── YES → Consider hybrid approach with TRACE + Analysis
       └── NO → Use TRACE Framework
```

## Hybrid Approaches

Sometimes a combination of frameworks provides the best approach. Consider these common hybrid patterns:

### Analysis + Knowledge Modeling
Best for: Complex problems requiring structured information representation
Example: System architecture analysis with component relationship mapping

### TRACE + Knowledge Modeling
Best for: Implementation projects with complex relationship modeling
Example: Building a data model implementation with entity relationships

### TRACE + Analysis
Best for: Implementation projects requiring thorough problem decomposition
Example: Building a solution after exploring multiple possible approaches

## Transition Examples

### From Analysis to Implementation

```
<!-- Using Analysis Framework -->
<analyze approach="component">
The authentication system requires these components:
1. Login service
2. Token management
3. User database interface
</analyze>

<!-- Transitioning to TRACE -->
Now let's implement this authentication system:

<understand>
We need to build an authentication system with login, token management, and database components.
</understand>

<scope_control>
Deliverables:
- Login service with basic authentication
- JWT token management
- Database interface layer
</scope_control>
```

### From Knowledge Modeling to Implementation

```
<!-- Using Knowledge Modeling -->
create_entities({
  entities: [{
    name: "User Authentication System",
    entityType: "Component",
    observations: [
      "Manages user login and sessions",
      "Requires secure password handling",
      "Must integrate with existing database"
    ]
  }]
});

<!-- Transitioning to TRACE -->
Let's implement the User Authentication System:

<understand>
We need to build a user authentication system that handles login, manages sessions, and integrates with the existing database.
</understand>

<scope_control>
Deliverables:
- Secure login endpoint
- Session management service
- Database integration layer
</scope_control>
```

## Style Guide Selection Tool Usage

1. Identify your primary goal (analysis, knowledge organization, or implementation)
2. Consider specific characteristics of your problem using the decision tree
3. Determine if a hybrid approach would be beneficial
4. Reference the transition examples if you need to switch between frameworks

Remember that you can always transition between frameworks as your project progresses from analysis to knowledge organization to implementation.
