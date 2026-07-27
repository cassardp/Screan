# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Screan is a web-based screenshot studio for App Store and Google Play listing screenshots: design text + device frames over uploaded screenshots, then export ZIPs in all required store formats. Pure frontend, no backend, no build step. Deployed at https://screan.app

## Running locally

Open `index.html` in a browser, or serve the folder with any static HTTP server (`python3 -m http.server`, `npx serve .`).

## Architecture

Module-based vanilla JavaScript on a global `App` namespace (entry `app.js`, modules in `js/`, modular CSS in `css/`). No framework, no bundler.

- **State**: centralized in `App.state`, organized by platform (iphone, ipad, mac, android-phone, android-tablet), each with its own screenshots and export formats.
- **Rendering**: Canvas 2D, dual mode (reduced-scale live preview, full-resolution export).
- **Persistence**: IndexedDB for the full app state (including image data); LocalStorage for the Claude API key, model choice and theme.
- **Localization**: per-screenshot content keyed by language code; batch AI translation calls the Anthropic API directly from the browser (default model `claude-haiku-4-5-20251001`, selectable from the live model list).

## External dependencies (CDN)

JSZip, Lucide icons, Google Fonts, Vercel Analytics.

## Conventions

- Vanilla JS with `var` declarations and the `App.` namespace pattern
- CSS custom properties for theming (`css/variables.css`), dark/light
- Communicate with the developer in French
