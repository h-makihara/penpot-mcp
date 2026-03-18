FROM node:24.11.1-slim

RUN apt-get update && apt-get install -y git && git clone https://github.com/penpot/penpot.git --branch mcp-prod --depth 1 && apt clean && rm -rf /var/lib/apt/lists/*
WORKDIR /penpot/mcp
RUN ./scripts/setup
CMD [ "pnpm", "run", "bootstrap" ]