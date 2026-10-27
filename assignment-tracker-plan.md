# My Assignment Tracker Dashboard — Plan

## Top-Level Overview

Build a single-page Streamlit dashboard titled **"My Assignment Tracker Dashboard"**.
The page displays three summary cards (Total Students, Submitted, Not Submitted) and one
Assignment Checklist table, all driven by hardcoded sample data. No backend, no database,
no file uploads — pure in-memory sample data only.

---

## Sub-Tasks

---

### Sub-Task 1 — Project Scaffold

**Intent**
Create the Streamlit app entry point and define the sample data that all other components
will consume. Establishing the data model first ensures every sub-task works from the same
source of truth.

**Expected Outcomes**
- `app.py` exists and runs without errors (`streamlit run app.py`)
- Page title is set to "My Assignment Tracker Dashboard"
- A sample dataset of students and their submission status is defined in-memory

**Todo List**
1. Create `app.py` with `st.set_page_config` setting the page title
2. Define sample data as a list of dicts (or a DataFrame) with columns:
   - `student_name` — string
   - `student_id` — string
   - `assignment_title` — string
   - `due_date` — date string
   - `submitted` — boolean
3. Derive three counts from the data:
   - `total_students` — len of dataset
   - `submitted_count` — count where submitted is True
   - `not_submitted_count` — count where submitted is False

**Relevant Context**
- No existing files; this is a greenfield project
- Sample data should contain at least 10 rows across 2–3 different assignments
  so the checklist is meaningful

**Status** — [ ] pending

---

### Sub-Task 2 — Summary Cards Row

**Intent**
Render the three metric cards at the top of the page so the user sees high-level
counts instantly on load.

**Expected Outcomes**
- Three cards displayed side-by-side in a single row
- Card 1: "Total Students" showing the total count
- Card 2: "Submitted" showing submitted count with a delta vs total
- Card 3: "Not Submitted" showing not-submitted count

**Todo List**
1. Create three Streamlit columns
2. In column 1, render `st.metric` for Total Students
3. In column 2, render `st.metric` for Submitted (value = count, delta label optional)
4. In column 3, render `st.metric` for Not Submitted

**Relevant Context**
- Derived counts come from Sub-Task 1
- `st.metric` is the standard Streamlit component for KPI cards

**Status** — [ ] pending

---

### Sub-Task 3 — Assignment Checklist

**Intent**
Display the full student assignment list as an interactive checklist/table so the user
can see every student's submission status and act on it.

**Expected Outcomes**
- A section titled "Assignment Checklist" appears below the summary cards
- Each row shows: Student Name, Student ID, Assignment Title, Due Date, Submitted status
- Submitted status is visually distinct (e.g. ✅ / ❌ or a color-coded badge)
- The table is filterable by submission status (All / Submitted / Not Submitted)

**Todo List**
1. Add a section header "Assignment Checklist" using `st.subheader`
2. Add a `st.selectbox` or `st.radio` filter: "Show: All / Submitted / Not Submitted"
3. Filter the DataFrame based on the selected option
4. Map the `submitted` boolean to a display symbol (✅ for True, ❌ for False)
5. Render the filtered data using `st.dataframe` or `st.table`

**Relevant Context**
- Data comes from Sub-Task 1
- Filter widget should sit directly above the table for clear visual grouping

**Status** — [ ] pending

---

### Sub-Task 4 — Styling and Layout Polish

**Intent**
Apply minimal visual polish so the dashboard looks clean and professional without
introducing external CSS frameworks or complex theming.

**Expected Outcomes**
- Page uses a wide layout so cards and table use full screen width
- A styled page header/title is visible at the top
- Visual separation between the cards section and the checklist section
- Color or icon cues reinforce Submitted vs Not Submitted at a glance

**Todo List**
1. Set `layout="wide"` in `st.set_page_config` (update Sub-Task 1 if not already set)
2. Render the dashboard title with `st.title` and a supporting `st.caption` or `st.markdown`
3. Add a `st.divider` between the summary cards and the checklist
4. Ensure Not Submitted metric uses a red delta or negative indicator to signal urgency

**Relevant Context**
- All styling should use native Streamlit components only
- No custom HTML/CSS injection unless absolutely necessary

**Status** — [ ] pending

---

## Sample Data Shape

| student_name | student_id | assignment_title      | due_date   | submitted |
|---|---|---|---|---|
| Alice Johnson | S001 | Essay on Climate Change | 2025-07-10 | True |
| Bob Smith | S002 | Essay on Climate Change | 2025-07-10 | False |
| Carol White | S003 | Math Problem Set 3 | 2025-07-12 | True |
| ... | ... | ... | ... | ... |

At least 10 rows, mixing submitted/not-submitted across 2–3 assignments.

---

## Non-Goals

- No authentication or login
- No file upload or external data source
- No database persistence
- No editing or deleting records from the UI
