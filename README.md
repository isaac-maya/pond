# pond

**A safe place for goose to swim.**

pond is an agentic environment for [goose](https://github.com/block/goose): a
one-command, open-source way to run goose inside its own isolated VM on your
machine, then drive it from the goose Desktop app you already use.

The agent lives in the pond. Your laptop stays outside it.

## Why

goose is genuinely useful, which is exactly why it's worth containing. An agent
that reads your filesystem, runs commands, and holds your API keys has your
whole machine as its blast radius. That's fine until the day it isn't.

pond shrinks the blast radius without shrinking what goose can do:

- **Isolated.** goose runs in a VM with no mount of your home directory. It
  can't reach your SSH keys, your git credentials, or the rest of your repos.
- **Still yours.** Your real goose Desktop connects to the pond over its normal
  interface. Same app, same sessions, same feel — the agent just isn't standing
  on your desk anymore.
- **One step.** Install, run one command, open Desktop. No hand-written
  cloud-init, no manual VM surgery, no "now edit this config file."
- **Open.** Provisioning you can read, reproduce, and change. No opaque box.

## What it is

At a high level, pond is three things:

1. **A provisioner** — creates a pinned, reproducible VM and installs goose
   inside it.
2. **A server** — runs goose's own desktop server inside the guest and exposes
   only that, securely, to the host.
3. **A connector** — points your local goose Desktop at the pond so the GUI you
   already use is talking to the goose that lives in the VM.

The VM becomes the home for the goose you're working on: its files, its
sessions, its keys, its mess.

## Scope, honestly

pond is about **blast radius**, not magic. Inside the pond, an agent still has
network access, still holds the provider keys you give it, and can still destroy
anything within its own disk. What it no longer has is your machine.

That distinction will stay explicit in the docs, because a sandbox that
overpromises is worse than one that doesn't exist.

## Status

Early. This repository is a placeholder while the design settles and code moves
in. Expect the shape above to get sharper, and expect the README to say less
than the code does once there is code.

## License

[Apache License 2.0](LICENSE) — the same license as goose and Lima. Permissive,
with an explicit patent grant.

Note that the guest operating system is a Fedora Linux image, which is a
collection of packages under their own licenses. Booting an official image does
not change pond's license; those terms stay inside the VM.
