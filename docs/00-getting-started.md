# Getting Started — Project 1: Git + GitHub

## Objective
Stand up a version-controlled home for everything we build, connected to a
public GitHub repo that can be shared on a résumé.

## Steps completed on the box
1. Configured global git identity (TODO: set your real name/email)
2. Generated an ed25519 SSH key for GitHub auth
3. Scaffolded this repo with README + roadmap

## Your actions (do these once)
1. Create a repo on GitHub named `homelab` (public).
2. Paste the SSH public key (printed by the setup script) into:
   GitHub -> Settings -> SSH and GPG keys -> New SSH key.
3. Link and push:
   ```
   cd ~/homelab
   git remote add origin git@github.com:<your-user>/homelab.git
   git add -A
   git commit -m "Initial homelab portfolio scaffold"
   git push -u origin main
   ```
4. Set your real git identity:
   ```
   git config --global user.name "Real Name"
   git config --global user.email "real@example.com"
   ```

## Next
Project 2: Containers with Podman — run a real service in a rootless container.
