# Planning Poker Tables Etude

An etude in the development of a collaborative **Planning Poker** tool supporting alignment, consensus, and coordination in Scrum Sprint planning.

## Overview

- **Tables**: Create a shared \"table\" for a Sprint planning session; a unique URL is generated and can be shared with the team.
- **Voting**: Developers choose story point estimates using a Fibonacci-style scale, vote in secret, then reveal together.
- **Roles**: Voter (default) and Observer; participants can switch roles at any time to match how they engage in the discussion.
- **Chat**: Real-time chat per \"round\", with optional round titles and history to capture the context of each estimate.
- **Participants**: Nickname-based identification, connection status indicators, and the ability to remove inactive participants to keep the table healthy.

The application focuses on helping teams surface different viewpoints, build shared understanding, and reach alignment on Sprint planning decisions. In this project, a \"table\" is a virtual room where a group plans together, and a \"round\" is a single estimation cycle between resets, typically corresponding to one user story or backlog item.

## Project Status

This repository is in an early phase. A draft specification is available under `docs/drafts/`. Implementation and technology choices will follow specification finalization.

## Documentation

- [Contributing guidelines](CONTRIBUTING.md) — commit format (Conventional Commits), PR titles, documentation and review practices, code quality and naming.
- [Draft specification](docs/drafts/specifications_rev1.draft.md) — detailed requirements (in Japanese).

## License

[MIT](LICENSE)
