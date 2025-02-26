# Analysis Framework Specification v2.0

*Created: 2025-02-26T05:48:00Z*  
*Last Modified: 2025-02-26T05:48:00Z*  
*Version: 2.0*

## Overview

The Analysis Framework provides a structured approach to breaking down complex problems through a sequence of cognitive stages. It ensures comprehensive, methodical, and transparent reasoning.

## Core Analysis Structure

The framework is built around five core analytical stages, each represented by a specific XML tag:

### 1. `<understand>` - Frame the challenge and context

**Purpose**: Establish a clear understanding of the problem, its context, and objectives before proceeding with analysis.

**Required Elements**:
- Core problem statement
- Key contextual factors
- Primary objectives

**Style Guidelines**:
- Clear, direct statements
- Sufficient background context
- Logical organization

**Attributes**:
- `depth="overview|detailed"` - Level of understanding depth
- `focus="problem|context|goals"` - Primary focus of the understanding phase

**MCP Integration**:
- Consider using knowledge_graph.search_nodes to retrieve relevant context
- Sequential thinking for problem breakdown

### 2. `<analyze>` - Break down components and relationships

**Purpose**: Systematically deconstruct the problem into its constituent parts and map relationships between them.

**Required Elements**:
- Component identification
- Relationship mapping
- Pattern recognition

**Style Guidelines**:
- Systematic approach
- Clear component delineation
- Visual representation when helpful

**Attributes**:
- `depth="surface|comprehensive"` - Depth of analysis
- `approach="component|system|comparative"` - Analysis methodology

**MCP Integration**:
- Use sequential_thinking to break complex problems into steps
- Consider knowledge_graph.create_entities for component mapping
- knowledge_graph.create_relations for relationship visualization
- github.search_code for relevant implementation examples

### 3. `<evaluate>` - Assess against criteria and alternatives

**Purpose**: Critically examine options against defined criteria to determine relative merit.

**Required Elements**:
- Evaluation criteria
- Alternative comparison
- Evidence-based assessment

**Style Guidelines**:
- Objective stance
- Clear criteria definitions
- Balanced perspective

**Attributes**:
- `criteria="specified evaluation framework"` - Criteria being used for evaluation
- `perspective="critical|balanced|supportive"` - Evaluation perspective

**MCP Integration**:
- sequential_thinking for methodical evaluation steps
- github.search_repositories for comparative solutions
- brave_web_search for external validation sources

### 4. `<decide>` - Select optimal path with justification

**Purpose**: Make a clear decision based on the evaluation, with transparent reasoning.

**Required Elements**:
- Clear decision statement
- Supporting rationale
- Addressing limitations

**Style Guidelines**:
- Decisive language
- Transparent reasoning
- Acknowledgment of tradeoffs

**Attributes**:
- `confidence="low|moderate|high"` - Confidence level in the decision
- `approach="elimination|weighted|intuitive"` - Decision methodology

**MCP Integration**:
- sequential_thinking for decision tree creation
- knowledge_graph.read_graph to incorporate established context

### 5. `<plan>` - Outline implementation strategy

**Purpose**: Create a concrete action plan for implementing the decision.

**Required Elements**:
- Action sequence
- Resource requirements
- Timeline considerations

**Style Guidelines**:
- Actionable steps
- Practical detail level
- Anticipatory of challenges

**Attributes**:
- `timeframe="immediate|short-term|long-term"` - Implementation timeline
- `detail="high-level|detailed"` - Plan detail level

**MCP Integration**:
- sequential_thinking for step-by-step implementation planning
- github.create_issues for task tracking recommendations
- github.create_or_update_file for documentation templates

## Component Registry

The framework includes a registry for extensions and integrations:

### Component Types

```xml
<component_types>
  <type id="mcp_adapter" interface="IMCPAdapter" />
  <type id="domain_extension" interface="IDomainExtension" />
  <type id="workflow_template" interface="IWorkflowTemplate" />
  <type id="visualization" interface="IVisualization" />
</component_types>
```

### Extension Points

```xml
<extension_points>
  <extension_point id="tag_customization">
    <description>Extend core tags with domain-specific elements</description>
    <interface>ITagExtension</interface>
  </extension_point>
  <extension_point id="workflow_stage">
    <description>Add custom stages to analysis workflows</description>
    <interface>IWorkflowStage</interface>
  </extension_point>
  <extension_point id="result_processor">
    <description>Process and transform MCP results</description>
    <interface>IResultProcessor</interface>
  </extension_point>
</extension_points>
```

## Context Awareness

The framework adapts to different contexts through parameter detection and adaptation rules:

### Context Parameters

```xml
<context_parameters>
  <parameter id="domain" type="string" default="general">
    <description>Problem domain or field of study</description>
    <examples>bioinformatics, finance, legal, engineering</examples>
  </parameter>
  
  <parameter id="complexity" type="enum" default="medium">
    <description>Complexity level of the analysis</description>
    <values>low, medium, high</values>
  </parameter>
  
  <parameter id="available_mcps" type="list">
    <description>MCPs available for current analysis</description>
    <detection>automatic</detection>
  </parameter>
  
  <parameter id="expertise_level" type="enum" default="intermediate">
    <description>User expertise with framework and domain</description>
    <values>beginner, intermediate, expert</values>
  </parameter>
</context_parameters>
```

### Adaptation Rules

```xml
<adaptation_rules>
  <rule id="domain_specialization">
    <condition>context.domain != "general"</condition>
    <action>activate_domain_extension(context.domain)</action>
  </rule>
  
  <rule id="complexity_adaptation">
    <condition>context.complexity == "high"</condition>
    <action>enable_advanced_components()</action>
  </rule>
  
  <rule id="mcp_availability">
    <condition>contains(context.available_mcps, "github")</condition>
    <action>enable_code_integration_features()</action>
  </rule>
  
  <rule id="expertise_adjustment">
    <condition>context.expertise_level == "beginner"</condition>
    <action>simplify_interface()</action>
  </rule>
</adaptation_rules>
```

### Progressive Disclosure

```xml
<progressive_disclosure>
  <level id="essential" expertise="beginner">
    <visible_components>
      <component>core_tags</component>
      <component>basic_mcps</component>
    </visible_components>
  </level>
  
  <level id="standard" expertise="intermediate">
    <visible_components>
      <component>core_tags</component>
      <component>all_mcps</component>
      <component>domain_extensions</component>
      <component>basic_workflows</component>
    </visible_components>
  </level>
  
  <level id="advanced" expertise="expert">
    <visible_components>
      <component>all_components</component>
    </visible_components>
  </level>
</progressive_disclosure>
```

## MCP Integration Guidelines

The framework provides detailed guidelines for integrating with Machine Cognition Primitives:

### Sequential Thinking

**When to use**:
- Complex problem decomposition
- Multi-step reasoning
- Decision trees with branching logic
- When revision of earlier thoughts may be necessary
- Error correction in reasoning chains

**Best practices**:
- Begin with estimated total_thoughts but adjust as needed
- Use isRevision when correcting earlier steps
- Consider branching when exploring alternative paths
- Set thoughtNumber and track progression explicitly
- End with clear conclusion and nextThoughtNeeded=false

**Integration examples**:
- Problem analysis: Break down requirements into logical steps
- Algorithm design: Map solution approach step-by-step
- Debugging: Trace through execution flow systematically

### Knowledge Graph

**When to use**:
- Mapping complex relationships between concepts
- Building persistent context across conversation
- Tracking entities and their attributes
- Creating visual relationship models
- Storing and retrieving structured information

**Best practices**:
- Create clear entity types for categorization
- Use descriptive relation types in active voice
- Add observations that enhance understanding
- Regularly read_graph to maintain context awareness
- Use search_nodes for targeted information retrieval

**Integration examples**:
- Project context: Store key stakeholders and requirements
- Technical analysis: Map system components and relationships
- Research synthesis: Connect related concepts and findings

### GitHub

**When to use**:
- Code example retrieval and creation
- Implementation recommendations
- Project structure analysis
- Development workflow suggestions
- Technical documentation generation

**Best practices**:
- Use search_repositories for finding relevant examples
- Leverage search_code for specific implementation patterns
- Consider create_issue for project management recommendations
- Examine list_commits for development history analysis
- Use get_file_contents to access specific implementations

**Integration examples**:
- Technical proposals: Create file templates with best practices
- Code reviews: Search similar patterns for comparison
- Implementation planning: Generate starter repositories or files

### Search

**When to use**:
- Fact verification
- Current information gathering
- Exploring alternatives
- Finding external resources
- Discovering best practices

**Best practices**:
- Construct specific queries for targeted results
- Use brave_web_search for general information
- Consider brave_local_search for location-specific queries
- Verify information from multiple sources when critical
- Integrate search findings with knowledge graph for persistence

**Integration examples**:
- Research phase: Gather relevant external information
- Verification: Confirm assumptions with authoritative sources
- Exploration: Discover alternative approaches or solutions

## MCP Result Processing

The framework includes components for handling and transforming MCP results:

```xml
<mcp_result_processing>
  <result_handlers>
    <handler for="sequential_thinking">
      <transformation>
        <extract>key_insights</extract>
        <format>structured_summary</format>
      </transformation>
      <visualization>thought_process_diagram</visualization>
      <storage>
        <primary>inline</primary>
        <secondary>knowledge_graph</secondary>
      </storage>
    </handler>
    
    <handler for="knowledge_graph">
      <transformation>
        <extract>entity_relationships</extract>
        <format>graph_visualization</format>
      </transformation>
      <visualization>relationship_diagram</visualization>
      <storage>
        <primary>persistent</primary>
      </storage>
    </handler>
    
    <handler for="github">
      <transformation>
        <extract>code_patterns</extract>
        <format>syntax_highlighted</format>
      </transformation>
      <visualization>code_snippet</visualization>
      <storage>
        <primary>inline</primary>
        <secondary>reference_system</secondary>
      </storage>
    </handler>
    
    <handler for="search">
      <transformation>
        <extract>key_information</extract>
        <format>structured_findings</format>
      </transformation>
      <visualization>information_card</visualization>
      <storage>
        <primary>inline</primary>
        <secondary>knowledge_graph</secondary>
      </storage>
    </handler>
  </result_handlers>
</mcp_result_processing>
```

## Cross-MCP Integration

The framework enables different MCPs to work together effectively:

```xml
<cross_mcp_integration>
  <integration_pattern id="sequential_to_knowledge">
    <source>sequential_thinking</source>
    <target>knowledge_graph</target>
    <mapping>
      <map from="thought" to="entity.observation" />
      <map from="thought_number" to="entity.metadata.sequence" />
    </mapping>
    <trigger>automatic</trigger>
  </integration_pattern>
  
  <integration_pattern id="search_to_sequential">
    <source>brave_web_search</source>
    <target>sequential_thinking</target>
    <mapping>
      <map from="search_result" to="thought.context" />
    </mapping>
    <trigger>manual</trigger>
  </integration_pattern>
</cross_mcp_integration>
```

## MCP Result Documentation

```xml
<mcp_result_documentation>
  <purpose>Document findings from MCP calls for reference</purpose>
  <format>
    <result_id>unique identifier for the result</result_id>
    <mcp_type>which MCP was used</mcp_type>
    <query>what was requested</query>
    <key_findings>summarized important discoveries</key_findings>
    <timestamp>when the call was made</timestamp>
  </format>
  <usage>
    - Reference result_id in subsequent analysis
    - Build on findings in follow-up MCP calls
    - Link related results to build comprehensive understanding
  </usage>
</mcp_result_documentation>
```

## Domain Specialization

The framework can be specialized for different domains:

```xml
<domain_specialization>
  <available_domains>
    <domain id="general">
      <name>General Analysis</name>
      <description>Default analysis patterns for general use</description>
    </domain>
    
    <domain id="bioinformatics">
      <name>Bioinformatics Analysis</name>
      <description>Specialized analysis for genomics and biological data</description>
      <vocabulary_extension>bio_terms.xml</vocabulary_extension>
      <tag_extensions>bio_tags.xml</tag_extensions>
    </domain>
    
    <domain id="finance">
      <name>Financial Analysis</name>
      <description>Specialized analysis for financial data and models</description>
      <vocabulary_extension>finance_terms.xml</vocabulary_extension>
      <tag_extensions>finance_tags.xml</tag_extensions>
    </domain>
    
    <domain id="software_engineering">
      <name>Software Engineering Analysis</name>
      <description>Specialized analysis for software systems and architecture</description>
      <vocabulary_extension>software_terms.xml</vocabulary_extension>
      <tag_extensions>software_tags.xml</tag_extensions>
    </domain>
  </available_domains>
</domain_specialization>
```

## Workflow Orchestration

The framework includes patterns for combining multiple MCPs in effective sequences:

```xml
<workflow_orchestration>
  <multi_mcp_workflow>
    <sequence>
      <step order="1">
        <action>Initial context gathering</action>
        <recommended_mcps>
          - knowledge_graph.read_graph
          - brave_web_search (if external context needed)
        </recommended_mcps>
      </step>
      <step order="2">
        <action>Problem decomposition</action>
        <recommended_mcps>
          - sequential_thinking to break down the challenge
        </recommended_mcps>
      </step>
      <step order="3">
        <action>Knowledge structuring</action>
        <recommended_mcps>
          - knowledge_graph.create_entities
          - knowledge_graph.create_relations
        </recommended_mcps>
      </step>
      <step order="4">
        <action>Implementation research</action>
        <recommended_mcps>
          - github.search_repositories
          - github.search_code
          - brave_web_search
        </recommended_mcps>
      </step>
      <step order="5">
        <action>Solution development</action>
        <recommended_mcps>
          - sequential_thinking for implementation steps
          - github.create_or_update_file for code creation
        </recommended_mcps>
      </step>
    </sequence>
    
    <integration_patterns>
      <pattern name="knowledge-driven reasoning">
        <description>Use knowledge graph to inform sequential thinking</description>
        <implementation>
          1. knowledge_graph.read_graph to establish context
          2. sequential_thinking to reason through the problem
          3. knowledge_graph.add_observations to document new insights
        </implementation>
      </pattern>
      
      <pattern name="evidence-based implementation">
        <description>Use search to inform GitHub operations</description>
        <implementation>
          1. brave_web_search to find best practices
          2. github.search_code to see implementations
          3. github.create_or_update_file to implement solution
        </implementation>
      </pattern>
    </integration_patterns>
  </multi_mcp_workflow>
</workflow_orchestration>
```

## Code Integration

The framework includes guidelines for effective code generation and integration:

```xml
<code_integration>
  <code_guidelines>
    <formatting>
      - Insert linebreak before code blocks
      - Use consistent indentation
      - Include clear comments
    </formatting>
    <attributes>
      language="specified programming language"
      purpose="example|implementation|validation"
      context="brief explanation"
    </attributes>
    <mcp_integration>
      - Use github.search_code for pattern examples
      - Consider github.get_file_contents for complete implementations
      - Use sequential_thinking for algorithm development
    </mcp_integration>
  </code_guidelines>
  
  <language_specific_guidelines>
    <language id="python">
      <style>PEP 8</style>
      <documentation>Google Docstring Format</documentation>
      <best_practices>
        - Type hints for function parameters and returns
        - Clear variable naming (descriptive_snake_case)
        - Function-based organization for modularity
        - Exception handling with specific exceptions
      </best_practices>
    </language>
    
    <language id="javascript">
      <style>Airbnb JavaScript Style Guide</style>
      <documentation>JSDoc</documentation>
      <best_practices>
        - ES6+ features for modern code
        - Async/await for asynchronous operations
        - Modular organization with imports/exports
        - Clear error handling with try/catch
      </best_practices>
    </language>
  </language_specific_guidelines>
</code_integration>
```

## Implementation Notes

This framework is designed to be continuously revised and improved. All updates should include:

1. Clear version numbering
2. Timestamped changes
3. Backward compatibility considerations
4. Integration with the Temporal Tracking System

The framework should evolve based on:
- Effectiveness in real-world analysis scenarios
- New capabilities and MCPs that become available
- Patterns that emerge from usage
- User feedback and success metrics

## Revision History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2025-01-15 | Initial framework specification |
| 2.0 | 2025-02-26 | Added temporal tracking integration, expanded MCP guidelines, and enhanced workflow orchestration |
