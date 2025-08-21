# Windsurf & Figma MCP Integration Guide

This guide provides best practices for collaborating with Cascade AI and Figma's Model Context Protocol (MCP) server in your project. It also outlines how to prompt Cascade for optimal results and leverage Windsurf's context-awareness features.

---

## 1. Set Up Figma MCP

To enable seamless Figma design-to-code workflows in Windsurf/Cascade:

1. **Ensure Figma Dev Mode is enabled** for your design files in **Figma's desktop app**. 
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/35b04093-4960-46b8-a4f2-1448ce46875b" />

2. **Connect the Figma MCP server**: Install the Figma MCP server from Cascade's MCP store
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/dc838596-0749-4b9b-9406-86a6146a1573" />


3. **Reference Figma node IDs**: When prompting Cascade, copy the node-id or the Figma URL in Dev Mode
<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/d8096166-775c-470b-bc0b-94efbb44cc3c" />


---

## 2. Prompt Guide: Figma-to-Code Collaboration

To achieve the best results when working with Cascade and Figma MCP:
- **Reduce the amount of context that windsurf eats**: 
By default, windsurf indexes the whole codebase for its context implication. It's better to provide concentrated version of codebase (like an architecture.md) to improve its execution speed and reduce the amount of tokens use.
 ```
 write up a architecture.md in the project root directory. it should include 
 1. files and folder structure
 2. the purpose of each component
 3. how does each service connect with each other
 output the file in .md format
 in your future response, refer to this file first
 ```
- **Be explicit about your design source and component structure**:
Provide the exact link of your dev ready figma component to windsurf and ask it to follow exactly the variables in it for best styling purpose. 
```
I now want you to implement <name of the widget>. You should refer to this figma component and use variables exactly like my figma files <link to your figma component>
you should implement it under <your destination directory>, and the resultant directory should be like
(provide your desired directory sturcture here)
├── YourComponent
│   ├── YourComponent.module.scss
│   ├── YourComponent.widget.tsx
│   └── index.ts
```
   

- **Provide context to iteract with other modules in the code base**:
Although by default, Cascade is gonna scan your whole code base for context. It's still better to directly pin context for any modules (e.g. translation, state management, http exchange, etc. ) you want to set up in the component.
```
you should use @filename as translation util and @filename as the key value pairs for multilingual support
you should refer to @filename and make async call to backend while loading data
you should write to app/src/store/xxx to set up a state for this compoenent, you can refer to @<filename_to_a_completed_component> for best practice
you should refer to this document @documentlink to set up the sylte of this component
... (more requirements, tell Cascade as detailed as possible as if you were to code it up yourself)
```
- **Use iterative refinement**: Provide feedback and request adjustments (e.g. color, spacing, font) referencing Figma node-ids for accuracy.

---

## 3. Best Practices for Windsurf Context Awareness

Referencing [Windsurf Docs: Context Awareness](https://docs.windsurf.com/context-awareness/overview):

- **Context Pinning**: Pin only the files or directories directly relevant to your current task. Over-pinning can slow down or confuse the model.

- **Pin for Task Dependency**: Pin module definitions, interface/config files, or directories with relevant code examples.

- **Current Focus Area**: Pin the directory with the majority of files you need for your session.

- **Testing**: Pin the file containing the class or component you are testing or extending.

- **Be Specific in Prompts**: The more precise your prompt (file names, node-ids, design requirements), the better Cascade can leverage context.

---
## 4. Reference
[official Windsurf context-awareness documentation](https://docs.windsurf.com/context-awareness/overview).
<br/>
[official Figma MCP guide](https://help.figma.com/hc/en-us/articles/32132100833559-Guide-to-the-Dev-Mode-MCP-Server)
