# Job Recruitment Portal — Candidate-Facing Screens

Low-fidelity wireframes covering the candidate journey end-to-end, built for
the Session 9 "Hands-On Activity," task 2: *"Build all candidate-facing
screens for the Job Recruitment Portal."*

## Screens

| # | Screen | Purpose |
|---|---|---|
| 1 | `01-job-search.png` | Browse and filter open roles (location, job type, experience level, salary) |
| 2 | `02-job-details.png` | Full job posting — description, responsibilities, requirements, company info, skills |
| 3 | `03-apply-for-job.png` | Application form — candidate info, resume/cover letter upload, screening question, submit |
| 4 | `04-my-applications.png` | Dashboard showing every application and its current status |
| 5 | `05-candidate-profile.png` | Candidate's own profile — resume, skills, work experience, education |

## Flow

```
Job Search  →  Job Details  →  Apply for Job  →  My Applications (status tracking)
                                                        ↑
                                                  Candidate Profile
                                                  (feeds resume/info into applications)
```

## Design notes

- Consistent left sidebar (Dashboard / My Applications / Saved Jobs / Referrals / Profile)
  once the candidate is logged in, so navigation doesn't change screen-to-screen
- Status badges on the dashboard (Applied, Under Review, Interview Scheduled, Rejected)
  match the states a `RepairTicket`-style status field would need in the data model —
  worth carrying that same status-tracking pattern into the schema/requirements doc
- These are structural wireframes (grayscale, no branding/color decisions) —
  recreate in **Penpot** or **Figma** for the actual submission, using these as
  the content/layout reference
