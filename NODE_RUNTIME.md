# Node.js development runtime

Use Node.js **22.23.4**, including the October 2026 security fixes (CVE-2026-111497). The `.nvmrc`, Travis configuration and package engine use the same version line.

Reference: https://nodejs.org/en/blog/vulnerability/october-2026-security-releases

Use Yarn 1 to preserve `yarn.lock`. Gulp 3 is kept compatible through a `graceful-fs@4.2.11` resolution; the obsolete `natives` resolution is removed. Only the documentation generator's Nunjucks dependency is updated within major 3 to remove its obsolete Node <=11 engine restriction. The changelog-only changez tool is updated to 3.0.1 to remove its unsupported `npm build` postinstall; release generation is not part of the security update validation.

Validation under Node 22.23.4: normal `yarn install`, Grunt build and ci-checks, the docs app Gulp build, and both i18n test suites (18 + 9 tests). Optional native extensions from the legacy toolchain emit build warnings on macOS arm64; Yarn installation still completes successfully.

The jqLite browser suite executes 6,215 tests on Chrome Headless 156, with 10 failures concerning datetime-local string normalization (omitted zero seconds/milliseconds). Full browser/remote SauceLabs coverage, complete documentation generation, changelog publishing, Firebase/GCS deployment and external Travis execution remain unverified. These results must not be described as a completely green browser suite.

The existing Travis deployment providers are restricted to the upstream `angular/angular.js` repository. This change adds no deployment trigger or target.
