# 🧠 AI Development Guidelines – Enterprise Next.js Project

These rules MUST be followed for all AI-generated code.

---

# 1️⃣ Core Stack

- Framework: Next.js (App Router)
- Language: TypeScript (strict mode)
- Styling: Tailwind CSS
- UI Library: shadcn/ui
- Data Fetching: React Query (@tanstack/react-query)
- Forms: React Hook Form
- Validation: Zod
- Toast System: Sonner
- Date Handling: date-fns
- Architecture: Smart / Dumb Component Pattern

---

# 2️⃣ Architecture Pattern

## Smart Components
- Handle:
  - React Query calls
  - Mutations
  - Form submission logic
  - Data transformation
- No heavy UI markup
- Located in:
  - /features/*
  - Route-level containers

## Dumb Components
- Pure presentational
- No API calls
- No business logic
- Fully typed props
- Reusable
- Located in:
  - /components/ui
  - /components/shared

Never mix business logic with UI.

---

# 3️⃣ React Query Rules (MANDATORY)

- NEVER use fetch inside useEffect
- Always use:
  - useQuery
  - useMutation
  - useInfiniteQuery when needed
- All queries must:
  - Have stable query keys
  - Handle loading state
  - Handle error state
  - Handle empty state
- Use optimistic updates where appropriate
- Invalidate queries properly
- Configure staleTime intentionally
- Create reusable hooks inside:
  - /hooks/queries

---

# 4️⃣ Forms Standard (React Hook Form + Zod)

## Form Rules

- ALWAYS use React Hook Form
- NEVER manage complex form state with useState
- All forms MUST:
  - Use zodResolver
  - Have schema validation using Zod
  - Infer types from Zod schema
  - Show validation errors clearly
  - Disable submit while submitting

## Validation Rules (Zod)

- All schemas must live in:
  - /lib/validations
- Never duplicate validation logic
- Use proper error messages
- Use refine() for complex validation
- Keep schemas reusable

---

# 5️⃣ Toast Rules (Sonner)

- Use Sonner for:
  - Success messages
  - Error messages
  - Warning messages
- Never use alert()
- Never expose raw backend errors
- Toasts must be:
  - Short
  - Clear
  - User-friendly

Trigger toast inside:
- Mutation onSuccess
- Mutation onError

---

# 6️⃣ Date Handling Rules (date-fns) – MANDATORY

## General Rules

- NEVER use native Date formatting manually
- NEVER use moment.js
- ALWAYS use date-fns utilities
- All date utilities must live in:
  - /lib/date.ts

## Formatting Rules

- Use format() for UI formatting
- Use parseISO() for parsing API dates
- Use differenceInDays(), differenceInMinutes(), etc. for calculations
- Use isBefore(), isAfter() for comparisons
- Use startOfDay(), endOfDay() for boundary logic

## Timezone Rules

- Backend must return ISO strings
- Always parse using parseISO()
- Avoid implicit timezone assumptions
- Display dates in user’s locale if required

## UI Date Standards

- Always format dates for readability:
  - Example: "dd MMM yyyy"
  - Example: "PPP" pattern
- Never show raw ISO strings in UI
- Date formatting must be centralized in helper functions

Example:
- formatDate()
- formatDateTime()
- formatRelativeTime()

---

# 7️⃣ shadcn/ui Rules

- Use shadcn components only
- Extend using className
- Do not edit core files
- Maintain built-in accessibility
- Use consistent variants
- Follow design token system

---

# 8️⃣ Responsiveness

- Mobile-first approach
- No fixed widths
- No horizontal overflow
- Flexible grid and flex layouts
- Proper spacing system (8px scale)
- Works from 320px to 2xl screens

---

# 9️⃣ Accessibility (NON-NEGOTIABLE)

- Semantic HTML required
- ARIA labels where necessary
- aria-invalid for form errors
- Keyboard accessible
- Visible focus states
- WCAG AA contrast compliance
- Proper alt text
- Never rely only on color

Forms must be fully accessible.

---

# 🔟 SEO (App Router)

- Use generateMetadata()
- Include:
  - title
  - description
  - openGraph
  - twitter
- One H1 per page
- Proper heading hierarchy
- Structured data (JSON-LD)
- Canonical URLs
- Optimize images with Next/Image

---

# 1️⃣1️⃣ GEO (AI Discoverability)

- Clear structured headings
- Short summaries
- FAQ sections when relevant
- Intent-driven content
- Machine-readable structure
- Avoid ambiguous text

---

# 1️⃣2️⃣ Dark & Light Theme

- Class-based theming
- Persist theme in localStorage
- Follow system preference
- No hardcoded colors
- Use design tokens
- Ensure accessibility in both themes

---

# 1️⃣3️⃣ Glassmorphism

- backdrop-blur
- Semi-transparent backgrounds
- Subtle borders
- Maintain readability
- Use sparingly

---

# 1️⃣4️⃣ Neumorphism

- Soft shadows
- Subtle elevation
- Minimal use
- Never reduce contrast

---

# 1️⃣5️⃣ Performance

- Prefer Server Components
- Client Components only when needed
- Lazy load heavy components
- Avoid unnecessary re-renders
- Optimize images
- Avoid layout shifts
- Lighthouse target 90+

---

# 1️⃣6️⃣ Code Quality

- Strict TypeScript
- No any
- Reusable utilities
- Centralized API layer
- No duplicated logic
- Proper error handling
- No console.log in production

---

# 🚫 DO NOT

- Fetch data inside UI components
- Use native Date formatting
- Show raw ISO strings
- Break accessibility
- Hardcode colors
- Mix business logic with UI
- Ignore loading/error states

---

# ✅ Priority Order

1. Accessibility
2. Performance
3. Clean Architecture
4. Scalability
5. SEO
6. Maintainability

All AI-generated code MUST follow these rules strictly.
