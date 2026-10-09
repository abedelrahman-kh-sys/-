# Instructions for Claude Code

## Use the project skills first

At the start of every conversation or task in this repository:

1. Read the user's request fully and work out the deliverable before acting.
   If the subject or the key input is missing, ask one short question.
2. Check the skills in `.claude/skills/` and use every one that matches the request,
   instead of working from general knowledge. Invoke them with the Skill tool.
3. The user writes in Arabic, Hebrew, or English. Reply in the language the user wrote in.

## Video requests

Any request to make, edit, caption, animate, or render a video, reel, or motion graphic:

1. Load `/hyperframes` first (the official HeyGen HyperFrames entry point). It routes to the right
   workflow (`/embedded-captions`, `/talking-head-recut`, `/general-video`, `/motion-graphics`, ...).
2. Also load `/video-editor`. It holds the user's personal reel style (9:16, captions, fonts,
   motion eases, editing pace). Apply it as the recommended defaults.
3. Render with the HyperFrames CLI (`/hyperframes-cli`).

HyperFrames compositions are local files. The HeyGen HyperFrames MCP `compose` / `render_video` tools
are only for hosted HeyGen projects. Use them only when the user asks for a project in the HeyGen app.

## Updating the HyperFrames skills

The HyperFrames skills are installed from `heygen-com/hyperframes` (pinned in `skills-lock.json`).
To update them: `npx skills update -p -y`. Do not edit those skill folders by hand.
Put personal changes in `.claude/skills/video-editor/` instead.
