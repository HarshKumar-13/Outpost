# Outpost – Agentic AI Workspace

**An AI-powered collaborative workspace where ideas become diagrams, documents, and actionable workflows.**

Outpost combines an intelligent AI agent, an interactive infinite canvas, and a collaborative document editor into one unified workspace. Users can interact with the AI agent using natural language to generate diagrams, create technical documentation, modify existing content, and organize ideas — while collaborating with their team in real time.

The AI agent works directly with the canvas and document editor, allowing it to understand existing content and perform contextual updates instead of simply generating text responses.

---

## Overview

Traditional productivity tools separate brainstorming, documentation, and collaboration across multiple applications.

Outpost brings these experiences together.

With Outpost, users can:

- Describe an idea and let AI transform it into a visual diagram.
- Generate structured documentation from natural language prompts.
- Edit documents and canvas elements through conversational AI.
- Collaborate with teammates in real time.
- Organize projects and workspaces using an integrated dashboard.
- Share workspaces through public read-only links.
- Export documents and canvas content as PDFs.

## Key Features

### 1. AI-Powered Workspace

- Integrated AI agent powered by Google Gemini.
- Natural language interaction for creating and modifying workspace content.
- Context-aware tool execution across documents and canvas.
- Ability to generate diagrams and structured documentation.
- Support for editing existing content through conversational instructions.

### 2. Interactive Infinite Canvas

- Built with the tldraw SDK.
- Infinite drawing and diagramming environment.
- Custom ERD table shapes.
- Editable database entities, columns, and relationships.
- Arrows and visual connectors.
- Real-time canvas synchronization.

### 3. Collaborative Document Editor

- Block-based rich-text editing powered by BlockNote.
- Real-time collaborative editing.
- Live cursor and editing synchronization.
- Yjs-powered document state management.
- AI-assisted document creation and modification.

### 4. Workspace Management

- Create and manage multiple workspaces.
- Integrated workspace dashboard.
- Kanban-style workspace organization.
- Drag-and-drop status management.
- Personal and organization-based workspaces.
- Persistent workspace data.

### 5. Team Collaboration

- Authentication powered by Clerk.
- Organization-based workspace access.
- Real-time document collaboration.
- Collaborative canvas experience.
- Public read-only workspace sharing.

### 6. Subscription and Usage Management

- Free and paid subscription plans.
- Usage tracking for AI prompts.
- Workspace limits.
- Feature-based access control.
- Subscription management through Clerk Billing.

### 7. Additional Capabilities

- Voice-based workspace creation.
- PDF export for documents and canvas.
- Public workspace sharing.
- Responsive application interface.

---

## Technology Stack

| Category                | Technologies                        |
| ----------------------- | ----------------------------------- |
| Frontend                | Next.js 16, React 19, TypeScript    |
| Styling                 | Tailwind CSS 4, shadcn/ui           |
| Authentication          | Clerk                               |
| AI Integration          | Google Gemini, Vercel AI SDK        |
| Database                | Supabase PostgreSQL                 |
| ORM                     | Prisma 7                            |
| Whiteboard              | tldraw SDK                          |
| Document Editor         | BlockNote                           |
| Real-time Collaboration | Yjs, Supabase Realtime, tldraw Sync |
| Billing                 | Clerk Billing                       |
| Canvas Sync Server      | Cloudflare Workers                  |
| Deployment              | Vercel                              |

---

## System Architecture

Outpost uses an agentic architecture where the AI model determines which tools to execute based on the user's request.

### AI Agent Workflow

1. The user submits a natural language prompt.
2. The application provides the agent with relevant workspace context.
3. Google Gemini interprets the request and selects the appropriate tools.
4. The browser executes the selected tools against the live canvas or document editor.
5. Changes are reflected in the workspace and synchronized with collaborators.

### Architecture Overview

```text
                  USER
                   |
                   v
            NEXT.JS APPLICATION
                   |
          +--------+--------+
          |                 |
          v                 v
    AI AGENT            WORKSPACE
          |                 |
          v          +------+------+
    GOOGLE GEMINI    |             |
          |          v             v
          v       DOCUMENT      CANVAS
    TOOL SELECTION  EDITOR       EDITOR
          |          |             |
          v          v             v
    BROWSER TOOL    Yjs         tldraw
    EXECUTION        |             |
          |          v             v
          |       SUPABASE     CLOUDFLARE
          |       REALTIME      WORKER
          |          |             |
          +----------+-------------+
                     |
                     v
              PERSISTENT DATA
                     |
                     v
               POSTGRESQL
                 (PRISMA)
```

**Important architectural detail:** AI tools operate against the live editor instances in the browser. This allows the agent to modify actual canvas and document content, rather than returning disconnected text or static diagram descriptions.

---

##

