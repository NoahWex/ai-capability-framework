# Style Guides

## Overview

This directory contains concise, focused style guides that provide structured templates for various AI assistance tasks. Unlike comprehensive frameworks, these style guides are designed to be:

- **Lightweight**: Quick to implement and understand
- **Focused**: Targeting specific assistance scenarios
- **Modular**: Easy to combine with other style guides
- **Templated**: Providing clear structure with XML tags

## Style Guide Format

Each style guide follows a consistent XML-based format that defines:

1. **Core Tags**: Primary structural elements with specific purposes
2. **Attributes**: Parameters that modify tag behavior
3. **MCP Integration**: Guidelines for integrating with Multi-Call Plugins
4. **Extension Points**: Places where the style guide can be extended

## Available Style Guides

- [TRACE.MCP.V.2.0](./trace_mcp_v2.xml) - Structured analysis framework with MCP integration
  - **Purpose**: Problem analysis with sequential thinking and knowledge integration
  - **Core Tags**: understand, analyze, evaluate, decide, plan
  - **Key Features**: MCP integration patterns, domain specialization, workflow orchestration

## When to Use Style Guides

- When you need a consistent approach to recurring task types
- To ensure all important aspects of a problem are covered
- When combining multiple AI capabilities (search, code, knowledge graph)
- For creating standardized outputs across similar scenarios

## Style Guide vs. Framework

While our [Project Management Framework](../project_management/project_management_framework.xml) provides comprehensive coverage of all project aspects, these style guides offer:

- Lower implementation overhead
- More focused guidance for specific scenarios
- Easier customization for particular domains
- Better integration with specific MCP capabilities

## Contributing

To add a new style guide:

1. Use the [Style Guide Template](./style_guide_template.xml) as a starting point
2. Focus on a specific problem domain or task type
3. Keep the structure concise and implementation-focused
4. Include clear MCP integration patterns where relevant
5. Document in this README when complete
