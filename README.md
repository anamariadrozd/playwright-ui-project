# Playwright E-commerce UI Tests

End-to-end UI automation for the [SauceDemo](https://www.saucedemo.com/) demo store, built with Playwright Test and JavaScript. The suite covers login, logout, product browsing and sorting, the shopping cart, and checkout validation and flow.

The tests use the Page Object Model: page classes keep locators and page actions together, while the specs describe user journeys and assertions. The suite is configured to run on Chromium, Firefox, and WebKit.

## Requirements

- Node.js and npm

## Install

From the project root, install the dependencies and the Playwright browsers:

```bash
npm ci
npx playwright install
```

## Run tests

Run the full suite on all configured browsers:

```bash
npm test
```

Run a single browser project:

```bash
npm test -- --project=chromium
npm test -- --project=firefox
npm test -- --project=webkit
```

Run one test file or filter tests by title:

```bash
npx playwright test tests/checkout.spec.js
npx playwright test --grep "without zip/postal code"
```

Run a test with the Playwright Inspector for interactive debugging:

```bash
npx playwright test tests/checkout.spec.js --project=webkit --grep "without zip/postal code" --debug
```

Open the HTML report after a run:

```bash
npx playwright show-report
```

## Project structure

```text
docs/                 Locator guidance
fixtures/             Playwright fixtures that provide page objects
pages/                Page Object Model classes and their locators/actions
test-data/            Demo user and checkout data
tests/                Login, logout, inventory, cart, and checkout specs
playwright.config.js  Browser projects and shared test settings
```

## Continuous integration

GitHub Actions runs the Playwright suite on pushes and pull requests targeting `main` or `master`. The workflow installs dependencies and browsers, runs the tests, and uploads the HTML report as an artifact.

## Notes

- The tests use the public SauceDemo demo site, so runs depend on that service being available.
- Playwright's WebKit project is useful for cross-browser testing on Windows; it is the Playwright-supported WebKit build, not the Safari application itself.
