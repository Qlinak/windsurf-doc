# Windsurf & Figma MCP Integration Guide

This guide provides best practices for collaborating with Cascade AI and Figma's Model Context Protocol (MCP) server in your project. It also outlines how to prompt Cascade for optimal results and leverage Windsurf's context-awareness features.

---

## 1. Set Up Figma MCP

To enable seamless Figma design-to-code workflows in Windsurf/Cascade:

1. **Ensure Figma Dev Mode is enabled** for your design files.

2. **Connect the Figma MCP server**: Install the Figma MCP server from Cascade's MCP store

3. **Reference Figma node IDs**: When prompting Cascade, copy the node-id or the Figma URL in Dev Mode

---

## 2. Prompt Guide: Figma-to-Code Collaboration

To achieve the best results when working with Cascade and Figma MCP:

- **Be explicit about your design source**:

 - Example:
   

- **Ask for component structure**:

 - Specify if you want index files, type definitions, or mock data included.

- **Use iterative refinement**:

 - Provide feedback and request adjustments (e.g. color, spacing, font) referencing Figma node-ids for accuracy.

- **Prompt Example**:

 ```

 Implement an Exchange Rate Table widget using the Figma design at node-id=1223-28896. Use SCSS modules, translation keys for all text, and match colors/fonts exactly. Include mock data and export via index.ts.

 ```

---

## 3. Best Practices for Windsurf Context Awareness

Referencing [Windsurf Docs: Context Awareness](https://docs.windsurf.com/context-awareness/overview):

- **Context Pinning**: Pin only the files or directories directly relevant to your current task. Over-pinning can slow down or confuse the model.

- **Pin for Task Dependency**: Pin module definitions, interface/config files, or directories with relevant code examples.

- **Current Focus Area**: Pin the directory with the majority of files you need for your session.

- **Testing**: Pin the file containing the class or component you are testing or extending.

- **Be Specific in Prompts**: The more precise your prompt (file names, node-ids, design requirements), the better Cascade can leverage context.

---

For more information, see the [official Windsurf context-awareness documentation](https://docs.windsurf.com/context-awareness/overview).
Overview - Windsurf Docs
On codebase context and related features
 
