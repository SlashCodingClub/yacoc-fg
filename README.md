# YACoC-fg

Yet Another Call of Cthulhu Frontend Game (YACoC-fg)

A Vue.js-based frontend application for a Call of Cthulhu themed game interface. This project features a real-time chat system with item interaction capabilities.

## Features

- Real-time chat system with message history
- Item interaction through a selection system
- Sender/Receiver message tracking
- Timestamp-based message logging
- Modern dark theme UI with Tailwind CSS

## Tech Stack

- Vue.js 3
- Tailwind CSS
- Axios for API communication
- JSON Server for backend mock data

## Preview

The application provides an immersive interface for players to:
- Send and receive messages
- Interact with game items
- Track actions with timestamps
- View message history with sender/receiver information


## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup
### Install PNPM

```sh
npm install -g pnpm
```

### Install Dependencies

```sh
pnpm install
```


### Run JSON Server (Backend Mock)

```sh
# Copy the example db.json file to db.json
cp db.example.json db.json

# Run the JSON server
pnpm json-server --watch db.json --port 3000
```


### Compile and Hot-Reload for Development

```sh
pnpm dev
```

### Compile and Minify for Production

```sh
pnpm build
```

### Lint with [ESLint](https://eslint.org/)

```sh
pnpm lint
```
