# Arno Store

A modern e-commerce project built with VTEX IO, utilizing SASS for CSS compilation.

## Table of Contents

- [Overview](#overview)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Development](#development)
- [Project Structure](#project-structure)
- [Available Scripts](#available-scripts)

## Overview

Arno Store is an e-commerce platform that leverages VTEX IO for its infrastructure. The project follows industry best practices with GitFlow for version control and SASS for maintainable styling.

## Prerequisites

Before you begin, ensure you have the following installed:

- Node.js (v14 or higher)
- npm or Yarn package manager
- Git
- VTEX Toolbelt CLI
- Git Flow extension

## Installation

1 **Clone the repository**

```bash
git clone <repository-url>
cd Arno-Store
```

2 **Install project dependencies**

```bash
npm install
# or
yarn
```

3 **Install SASS globally**

```bash
npm install -g sass
# or
yarn global add sass
```

## Development

### SASS/SCSS Architecture

The project uses SASS for styling with the following structure:

- **React Components Styles**:

  - Source: `react/styles/` and `react/styles/components/`
  - Output: `react/` and `react/components/` as `.css` files

- **Global Styles**:
  - Source: `styles/scss/`
  - Output: `styles/css/` as `.css` files

### Watching SCSS Files

To automatically compile SCSS files on changes:

```bash
npm run sass
# or
yarn run sass
```

### Development Mode

Run both SASS watcher and VTEX link simultaneously:

```bash
yarn dev
```

This command is recommended for active development as it handles both styling compilation and VTEX workspace linking.

## Project Structure

```text
Arno-Store/
├── additional/
├── assets/
├── conteudo enriquecido/
├── docs/
├── emails_transacionais/
├── graphql/
├── node/
├── react/
│   ├── components/
│   └── styles/
│       └── components/
├── store/
│   ├── blocks/
│   ├── interfaces.json
│   └── routes.json
├── styles/
│   ├── configs/
│   ├── css/
│   ├── iconpacks/
│   └── scss/
└── package.json
```

## Available Scripts

- `npm run sass` / `yarn sass` - Watch and compile SCSS files
- `yarn dev` - Run SASS watcher and VTEX link concurrently
- `vtex link` - Link your workspace to VTEX