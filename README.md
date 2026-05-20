# NachUI Agent Skills

Welcome to the **NachUI Agent Skills** repository! This is a curated collection of agentic instructions, rules, and playbooks that extend the capabilities of AI coding agents (such as Antigravity) specifically for the NachUI ecosystem.

By adding these skills, you ensure that coding assistants understand NachUI's visual aesthetic, coding standards, CLI structure, and testing guidelines out-of-the-box.

---

## 🚀 Available Skills

This repository contains the following skills:

### 🎨 [nachui-design](./nachui-design/SKILL.md)

- **Description:** Governs all UI styling, themes, colors, and layout principles.
- **Key Features:** Clean Clinical Minimalist aesthetic guidelines, OKLCH color token palettes, responsive border-radius logic (`--radius`), dark mode strategies, accessibility guidelines, and theme accent overrides (Zinc, Blue, Green, Rose).

### 🛠️ [nachui-component-development](./nachui-component-development/SKILL.md)

- **Description:** Playbook for developing high-fidelity React 19 / Next.js components.
- **Key Features:** Server/Client component selection rules, Tailwind CSS v4 styling rules, `class-variance-authority` (CVA) isolation, Framer Motion constant optimization, `forwardRef` types, context safety throwing, and import group ordering.

### 🧪 [nachui-testing-playbook](./nachui-testing-playbook/SKILL.md)

- **Description:** Guide to writing and running automated unit and integration tests.
- **Key Features:** Vitest and React Testing Library conventions, mock guidelines, execution commands via pnpm workspace filters, user interaction simulation, and accessibility-first selectors.

### 📝 [nachui-docs-management](./nachui-docs-management/SKILL.md)

- **Description:** Guides page modifications and content operations for the documentation application.
- **Key Features:** Next.js 16 structure, `@content-collections` MDX compilation cache handling, deterministic component rules to prevent React SSR hydration mismatches, next-intl, and environment secrets management.

### 💻 [nachui-cli-development](./nachui-cli-development/SKILL.md)

- **Description:** Guide to developing and extending the official NachUI CLI.
- **Key Features:** Commander routing, dynamic subcommand imports, Clack prompts, console styling with Kleur, spin states, Zod parameters validation, and ESM/CJS build compilation using `tsup`.

---

## 📦 How to Install and Use

### Option 1: Using the Agent Skills CLI (Recommended)

You can install these skills directly into your workspace from this repository.

Run the following command from the root of your target project:

```bash
# Install the entire suite of skills
npx skills add github:figueroaignacio/ui-skills

# Install a specific skill (e.g., nachui-design)
npx skills add github:figueroaignacio/ui-skills/nachui-design
```

This will download the skills to your project's `.agents/skills/` directory and lock their versions in your `skills-lock.json` file.

### Option 2: Manual Installation

Alternatively, clone or copy the folders from this repository directly into your project's `.agents/skills/` directory:

```text
your-project/
└── .agents/
    └── skills/
        ├── nachui-design/
        ├── nachui-component-development/
        ├── nachui-testing-playbook/
        ├── nachui-docs-management/
        └── nachui-cli-development/
```

Once placed, compatible agentic coding assistants will automatically detect and follow these guidelines.

---

## ✍️ How to Author a New Skill

To add a new skill to this repository, organize it as a self-contained directory containing a `SKILL.md` file:

1. **Create a Directory:** `skills/my-new-skill/`
2. **Add a `SKILL.md` file** with YAML frontmatter at the very top:

   ```markdown
   ---
   name: 'my-new-skill'
   description: 'Use when performing tasks related to...'
   ---

   # Detailed instructions here

   Add rules, best practices, checklists, and code templates.
   ```

   > [!IMPORTANT]
   > The `description` field is crucial. AI routing mechanisms parse it to decide when to activate the skill. Write it clearly so the agent knows precisely when it is relevant.

3. _(Optional)_ Add supporting directories inside your skill folder:
   - `scripts/` — Executable files/scripts that automate tasks for the skill.
   - `references/` — Heavy checklists, manuals, or external spec sheets.
   - `assets/` — Templates, configuration snippets, or visual diagrams.
