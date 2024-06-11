# TLDR
Focus Zone is a minimalistic productivity app designed to help users reduce distractions,  enhance their concentration, and achieve mindfulness through structured routines, screen time management, and personalised insights

# Technical Implementation
[Add Flow Chart]

[Add Sequence Diagram]

## Abstractions
- View Models
	- Used for state management across the whole app, similar to a context in React. 
	- The states which map from the database, interact via a repository. 
	- Use `BaseViewModel` to get access to `fetch`, `delete`, `create`, `update`
- Database Interactions
	- Interact via `CommonRepository` - `addAsync, getAsync, getAllAsync, deleteAsync`

# Tasks Remaining
MVP
- [x] add abstractions
	- [x] database interactions (repository)
- [x] Analyse how to test this app
	- [ ] Test creating a routine
- [ ] Create Logo + Website
- [ ] Create Flow Chart of App/Documentation/Customer Journey

Future
- [ ] Add Break Difficulties
