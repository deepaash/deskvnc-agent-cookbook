# DeskVNC agent cookbook

A small, copy-pasteable cookbook for driving Windows, Linux and macOS
desktops through the [DeskVNC](https://github.com/psmux/DeskVNC) MCP
server. The gists linked from this README are self-contained: each one
is a single file you can open on its own, paste into your editor, and
use without reading the others.

DeskVNCViewer is a native desktop client for VNC, RDP and SSH, written
in Rust on Tauri 2, that ships an MCP server named `dvv` inside the
app. The server lets an AI agent open one of your saved machines,
observe the screen and send clicks and keystrokes over the ordinary
VNC, RDP or SSH connection, with nothing installed on the remote
target and a person able to take the wheel back at any moment. The
`dvv` binary is the same surface whether the agent reaches it as MCP
tools or as shell commands.

## The cookbook, in six files

| Gist | One line |
| --- | --- |
| [`dvv-shell-cheatsheet.sh`](https://gist.github.com/deepaash/1df820439f0689347658c0bf7f403006) | The complete `dvv` shell cheatsheet, every command from discovery to teardown with one-line descriptions, copy-pasteable. |
| [`mcp-client-configs.json`](https://gist.github.com/deepaash/7996655447b174008d4995a79015fb40) | Ready-to-paste DeskVNC MCP config snippets for Claude Code, OpenCode, Codex CLI, Cursor, Windsurf, VS Code, Gemini CLI and Python MCP clients, using the real macOS binary path. |
| [`agent-system-prompt.md`](https://gist.github.com/deepaash/9a3948a1512df5660fbcf7816606254e) | A system prompt that teaches any AI agent the DeskVNC observe-then-act loop, the generation fence, the scale rule, and how to recover from `LIMB_GONE`, `SCREEN_CHANGED` and `LEASE_REVOKED`. |
| [`coordinate-fencing.md`](https://gist.github.com/deepaash/785a0fd38d44756a0da80cb1e3811f3a) | DeskVNC coordinate fencing reference: the geometry and content generation fences, the `imageSpace` line, and worked click arithmetic at scale 0.5 and 0.25. |
| [`protocol-cheatsheet.md`](https://gist.github.com/deepaash/77fd6d9b5cce58680f05d9b09307849f) | DeskVNC protocol cheat sheet: RFB versions and encodings, VeNCrypt, RA2, Apple authentication, NLA, RemoteApp, RDP codecs, SSH keys, and what the VNC, RDP and SSH cores speak. |
| [`boundary-attended-support.md`](https://gist.github.com/deepaash/9fc5fc69e0a722d2c7e5364847aa73eb) | DeskVNC attended support with Boundary: the handshake in numbered steps, the four digit code service format, the invitation fallback, and the recipient's revocation and termination rules. |

## A minimal path through the set

If you are new to the agent plane and want to wire it up in fifteen
minutes, this is the order that holds together:

1. Install DeskVNCViewer, open it once, save a machine with its
   password. The release page is
   <https://github.com/psmux/DeskVNC/releases/latest>.
2. Paste the relevant block from
   [`mcp-client-configs.json`](https://gist.github.com/deepaash/7996655447b174008d4995a79015fb40)
   into your MCP client. The macOS path is verified; the Linux and
   Windows paths are the documented install locations.
3. Use [`dvv-shell-cheatsheet.sh`](https://gist.github.com/deepaash/1df820439f0689347658c0bf7f403006)
   when you want a tight command list without the prose.
4. If you build your own agent, paste
   [`agent-system-prompt.md`](https://gist.github.com/deepaash/9a3948a1512df5660fbcf7816606254e)
   into the system prompt. It carries the loop order, the generation
   fence, the scale rule and the three error codes an agent has to
   handle.
5. When a click lands in the wrong place, read
   [`coordinate-fencing.md`](https://gist.github.com/deepaash/785a0fd38d44756a0da80cb1e3811f3a)
   to be sure the scale and the `generation` were correct.
6. When you are handing a machine to a person outside your network,
   use [`boundary-attended-support.md`](https://gist.github.com/deepaash/9fc5fc69e0a722d2c7e5364847aa73eb)
   for the short code service handoff and the longer invitation
   handoff.
7. For a deeper look at what the three protocol cores speak, read
   [`protocol-cheatsheet.md`](https://gist.github.com/deepaash/77fd6d9b5cce58680f05d9b09307849f).

## A note on what is verified

Every gisted file in this cookbook traces back to one of two sources:
the project's `docs/AGENTS.md` and `docs/ARCHITECTURE.md` (and the
agent skill at `skills/deskvnc/SKILL.md`), and the published README
on the DeskVNC repository. The MCP tool surface, the binary paths,
the loop order, the fence names, the error codes, the protocol
coverage and the Boundary handoff are all on those pages. Where a
number came from a measured workflow (the 19 ms observe-then-act
cycle, the 25 ms screenshot at `scale: 0.25`, the 447 characters a
second typing throughput), it is a number that appears in the
project's own published workflow, not a derived estimate.

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md)
for the shape of a good change.

## License

This cookbook is released under the MIT License. See
[LICENSE](./LICENSE) for the full text.

The DeskVNC project that this cookbook accompanies is dual licensed
under MIT OR Apache-2.0; the cookbook itself is MIT only so it stays
simple to reuse in any project.
