FROM oven/bun:1

WORKDIR /app

COPY package.json bun.lock ./
RUN bun install --frozen-lockfile

COPY . .

# Warm Vite's dep-optimizer cache at build time so the first request after a
# deploy is not the one that pays for bundling the dependency tree.
# Note: /index.json answers immediately; /iframe.html is what triggers the
# optimizer. Never probe /mcp here — a GET without `Accept: text/html` opens
# an SSE stream and blocks forever.
RUN PUBLIC_MCP=1 bun run storybook -- -p 6006 --ci --quiet & \
    bun -e ' \
      const wait = async (url) => { \
        for (let i = 0; i < 180; i++) { \
          try { const r = await fetch(url); if (r.ok) { await r.text(); return true } } catch {} \
          await Bun.sleep(5000); \
        } \
        return false; \
      }; \
      if (!await wait("http://localhost:6006/index.json")) process.exit(1); \
      await wait("http://localhost:6006/iframe.html"); \
    '; \
    kill %1 2>/dev/null; true

ENV PUBLIC_MCP=1
ENV NODE_OPTIONS=--max-old-space-size=4096
EXPOSE 6006

CMD ["bun", "run", "storybook", "--", "-p", "6006", "--host", "0.0.0.0", "--ci", "--quiet"]
