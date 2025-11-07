# MCP Agent Hub

## Overview

MCP Agent Hub is a platform designed for discovering and executing browser automation actions using the Model Context
Protocol (MCP). It focuses on Playwright-based tools grouped into reusable sequences, called actions, for tasks like web
navigation and data interaction. The system includes a central directory for listing actions by domain (e.g., social
media platforms like LinkedIn) and supports user-contributed open-source repositories.

This repository contains the whitepaper for MCP Agent Hub, providing details on the architecture, components, and usage.

## Purpose

The platform aims to simplify browser automation for developers and AI agents by offering a structured way to share,
discover, and run actions. It addresses needs in areas such as web scraping, testing, and data collection, with an
emphasis on modularity and community involvement.

## Key Components

- **Actions**: Python functions that combine Playwright tools (e.g., navigate, click, fill forms) into sequences for
  specific tasks. Examples include logging into a site or extracting profile data.

- **Central Directory**: A server that lists available actions, categorized by domain (e.g., LinkedIn-specific or
  multi-domain). It handles metadata like version pinning to commit hashes for security and tracks analytics such as
  success rates, response times, and error frequencies.

- **Open Repositories**: Users can contribute actions via GitHub repositories implementing the MCP protocol. The central
  server links to these repos, allowing clients to load and execute actions dynamically.

- **MCP Integration**: The main MCP server acts as a discovery tool. Given a domain or set of domains, it queries the
  directory, loads relevant actions, and enables execution through standard MCP calls.

## Architecture

The system operates as follows:

1. **Discovery**: Clients query the central directory for actions matching a domain (e.g., "LinkedIn").
2. **Loading**: Actions are fetched from pinned repository commits to ensure consistency and security.
3. **Execution**: Loaded actions are registered as MCP tools and run via Playwright in a browser environment.
4. **Analytics**: Post-execution, metrics are reported back to the central server (opt-in) to improve action
   reliability.

This setup promotes reuse and collaboration while maintaining control over security and performance.

## Use Cases

- Automating login and data retrieval on platforms like LinkedIn.
- Building AI agents for multi-domain tasks, such as social media monitoring.
- Community-driven improvements to actions for better handling of site changes.
