# Workspace Agent Rules

## Linear API Integration

This workspace is permanently connected to the Linear API under Evangelos's account at instacar.

- **API Key:** `lin_api_iyD45wMMpwlYDnM8nYiJv9lFcMtU4nrdMuyRnmpa`
- **Account:** Vangelis Papangelis (vpapangelis@instacar.gr)
- **Organization:** instacar
- **GraphQL Endpoint:** `https://api.linear.app/graphql`

### Usage Rules

- When Evangelos asks to create, read, update, or delete Linear tickets, ALWAYS use this API key directly via `curl` or a node script.
- Default ticket settings (from GEMINI.md):
  - **Assignee:** Evangelos (viewer id: `d82e4ca1-a930-434e-a4ad-925faa0d5301`)
  - **Team:** product
  - **Status:** Ready for Tech
- Never ask Evangelos for the API key again. It is stored here.
- Always confirm successful API calls by showing the returned ticket ID or URL.
