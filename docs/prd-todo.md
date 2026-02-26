# Product Requirements Document (PRD) - Todo App Upgrade: Due Dates, Priorities, and Filters

## 1. Overview

We are upgrading the existing basic Todo app (currently only supporting title and completed state) to make it more practical for everyday task management while remaining simple and teachable. The upgrade will introduce due dates, priority levels, and basic filtering so users can quickly see what is urgent today, what is overdue, and which tasks are most important, all without adding backend complexity or multi-user features.

---

## 2. MVP Scope

- **Data Model**
  - Task fields:
    - `title`: required.
    - `priority`: `"P1" | "P2" | "P3"`, default `"P3"`.
    - `dueDate`: optional, ISO `YYYY-MM-DD`.
  - Validation:
    - Invalid `dueDate` values are ignored and treated as if `dueDate` is absent.
- **Task Creation & Editing**
  - Users can:
    - Create a new task with a required title.
    - Optionally assign a `dueDate` using a `YYYY-MM-DD` style date input.
    - Set or change the `priority` (P1, P2, P3), defaulting to P3 when not specified.
- **Task Display**
  - Each task clearly displays:
    - Title.
    - Completion status (existing behavior).
    - Priority label (P1, P2, or P3).
    - Due date, if present.
  - Priority is visually indicated (e.g., distinct color badges such as red for P1, orange for P2, gray for P3), as long as implementation remains simple.
- **Filters / Views**
  - Provide three primary views, accessible via tabs or buttons:
    - **All**:
      - Shows all tasks, including completed and incomplete.
      - Shows tasks regardless of due date.
    - **Today**:
      - Shows only incomplete tasks whose `dueDate` is equal to “today” (based on local date).
    - **Overdue**:
      - Shows only incomplete tasks whose `dueDate` is before “today”.
- **Storage & Architecture**
  - All task data is stored locally (e.g., browser local storage).
  - No backend services, APIs, or external storage are introduced.
  - No changes are required to the existing backend.

---

## 3. Post-MVP Scope

- **Overdue Visual Highlighting**
  - Overdue tasks are visually emphasized (e.g., highlighted in red or with a strong visual indicator) to stand out clearly from non-overdue tasks.
- **Sorting Behavior**
  - Standardized sort order across views where applicable:
    1. Overdue tasks appear before non-overdue tasks.
    2. Within each group, tasks are ordered by priority: P1 → P2 → P3.
    3. Within the same priority, tasks are ordered by due date ascending (earlier dates first).
    4. Tasks without a `dueDate` appear after all tasks with a `dueDate`.

---

## 4. Out of Scope

- Notifications (email, push, in-app reminders).
- Recurring or repeating tasks.
- Multi-user support or shared task lists.
- Keyboard navigation or advanced accessibility features beyond basic browser defaults.
- Any backend or server-side changes.
- Any external or cloud storage; the app remains strictly local-storage based.
