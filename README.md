# Opinionated web-staking for xx Network

**NOTE:** this repository is experimental and does not provide any additional features. Please use upstream repository for default features.

## Description

`web-staking` is a web application designed to facilitate the staking of `xx` tokens. It provides an intuitive interface for users to seamlessly interact with the staking process.

## Table of Contents

- [Opinionated web-staking for xx Network](#opinionated-web-staking-for-xx-network)
  - [Description](#description)
  - [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [Usage](#usage)
  - [Scripts](#scripts)
  - [Dependencies](#dependencies)
  - [Development](#development)
    - [Project Structure](#project-structure)
    - [Environment Variables](#environment-variables)
      - [Node list](#node-list)
    - [Build Process](#build-process)
  - [Contributing](#contributing)
    - [Guidelines](#guidelines)
  - [License](#license)
  - [Contact](#contact)

## Installation

To get started with `web-staking`, follow these steps:

1. Clone the repository:

   ```bash
   git clone https://github.com/armchairancap/web-staking
   ```

2. Navigate to the project directory:

   ```bash
   cd web-staking
   ```

3. Install the necessary dependencies:
   ```bash
   yarn
   ```

## Usage

To start the application in development mode, use:

```bash
yarn start
```

The development server will run on port `3000`. Open your browser and navigate to `http://localhost:3000` to access the application.

## Scripts

The following scripts are available in the `package.json` file for development and production tasks:

- `start`: Launches the development server.
- `build`: Compiles the project using `react-app-rewired`.
- `test`: Runs the test suite.
- `eject`: Ejects the create-react-app configuration.
- `lint`: Checks the code for quality issues using ESLint.

## Dependencies

Key dependencies used in this project include:

- **React** and **React-DOM**: For building the user interface.
- **@apollo/client**: Manages GraphQL data.
- **@polkadot/api**: Interacts with the Polkadot blockchain.
- **@mui/material**: Provides Material-UI components.
- **Redux Toolkit**: Handles application state.

For a comprehensive list, refer to the `package.json` file.

## Development

The project is configured with tools and standards to ensure smooth collaboration and efficient development.

The project is configured to use TypeScript, with settings defined in `tsconfig.json`. It also uses ESLint and Prettier for code quality and formatting.

### Project Structure

```plaintext
src/
├── @types             # TypeScript definitions and type augmentations.
├── App.tsx            # Root React component.
├── assets             # Static assets like images, logos, and icons.
├── augment-types      # TypeScript type augmentation files.
├── components         # Modular and reusable UI components.
├── custom-derives     # Custom derived data from the Polkadot API.
├── dayjs.ts           # Configuration for the Day.js library.
├── hooks              # Custom React hooks for shared logic.
├── index.tsx          # Entry point for the React application.
├── pages              # Page components representing application routes.
├── plugins            # Configuration and setup for external libraries.
├── schemas            # GraphQL schemas and queries.
├── simple-staking     # Logic and components specific to the staking feature.
├── sleeve             # Custom Polkadot WASM crypto implementations.
├── theme              # Configuration for the Material-UI theme.
├── types.ts           # Application-wide TypeScript types.
└── utils              # General-purpose utility functions.
```

### Environment Variables

Environment variables are listed in the `.env-example` file. Here are the key variables:

```properties
REACT_APP_API_URL=wss://rpc.xx.network
REACT_APP_BACKEND_HOST=xxexplorer-prod.hasura.app
REACT_APP_WALLET_URL=https://wallet.xx.network
NODE_LIST_URL=https://raw.githubusercontent.com/armchairancap/web-staking/refs/heads/master/node_list.json
```

Note that using remote servers means slow(er) performance, but having your own means you need to run an archive chain node and an indexer (`REACT_APP_BACKEND_HOST`), which isn't trivial (needs few hundred GB of SSD capacity and at least two VMs). 

#### Node list

`NODE_LIST_URL` is is the main difference versus upstream - it is supposed to hold a list of whitelisted or blacklisted nodes.

It can look similar to this.

```json
{
    "whitelist": [
        {
            "POOL": "armchairancap",
            "ON_CHAIN_ID": "armchairancap-alfa",
            "WALLET": "6ZtD5PG1AEHiKiVWWGJkLU9jG4wemR7kzwVJVxcRf7pmVNYp",
            "CMIX_ID": "LZAsnNWehPngLTur0FnORANOzHraOZlg8O/LXXx0BJoC"
        }
    ],
    "blacklist": [
        {
            "POOL": "moneyteam",
            "ON_CHAIN_ID": "moneyteam 01",
            "WALLET": "6ZsGpqy3LA6HWm2MXS31vqmJnxfaXLvwEgr4Tw6d9yJQNtkM",
            "CMIX_ID": "3XZ5lNaFv5OgAgXi9O7pZANP/CWyGpbhB9E8QmYM1sMC"
        }
    ]
}
```

### Build Process

The project uses `react-app-rewired` for builds (with [yarn](https://yarnpkg.com/getting-started/install)):

```bash
yarn build
```

If you use NPM, you may encounter errors such as [this one](https://github.com/armchairancap/web-staking/issues/2) with NodeJS 23.3.0. Even `yarn build` fails if simple-staking/section.ts is modified to load data from file or URL (issue [3](https://github.com/armchairancap/web-staking/issues/3)).

Build artifacts are output to the `build/` folder.

## Contributing

Contributions are welcome! Please follow these steps to contribute:

1. **Fork the repository**.
2. **Create a new branch** for your feature or bugfix (e.g., `feature/add-new-feature` or `bugfix/fix-issue`).
3. **Commit your changes** with descriptive messages.
4. **Push your branch** to your fork.
5. **Submit a pull request (PR)** with the following structure:
   - **Changes**: Summary of changes made.
   - **Reason**: Explanation of why these changes are necessary.
   - **Tag**: Choose from the following:
     - `bug`: Fixes a bug.
     - `feature`: Adds new functionality.
     - `improvement`: Enhances existing functionality.
     - `docs`: Documentation updates.
     - `test`: Adds or modifies tests.
     - `refactor`: Code restructuring without functional changes.
     - `chore`: Minor maintenance tasks.
     - `style`: Formatting changes with no code logic alterations.
     - `performance`: Performance optimizations.

### Guidelines

- Follow the repository's coding style.
- Write clear commit messages (e.g., "Fix: Resolved staking issue").
- Include relevant tests for your changes.
- Ensure no existing functionality is broken by your contributions.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Contact

If you want to contribute, create a pull request or submit an issue.

