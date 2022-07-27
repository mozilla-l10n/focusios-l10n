# Focus by Firefox localization

This repository hosts the localization for the Focus by Firefox project for iOS.

The application code with build instructions can be found at https://github.com/mozilla-mobile/focus-ios

Localization only happens via [Pontoon](https://pontoon.mozilla.org/projects/focus-for-ios/).

## For Developers

If your PR touches many files (such as string exports that need to be localized), it will get stale very quickly because many contributors add to these files. Please make sure there is someone around to merge your PR in a timely manner, or expect to need to update your PR to resolve conflicts.

## String updates

Automation is used to extract strings from the code repository, and expose them to all other locales.

1. Strings are extracted and saved in the `en-US` XLIFF file.
2. The updated `en-US` XLIFF is used as a template. Existing translations are copied over if all these elements match:
    * `id` attribute of `trans-unit`.
    * `original` attribute of `file`.
    * `source` text.

As a consequence, the default update removes translations if:
* The source text was changed.
* The string was moved from one file to another.

This is not ideal when the change in the source text is trivial, or the string move is caused by code refactoring.

It’s possible to invoke [automation manually](https://github.com/mozilla-l10n/focusios-l10n/actions/workflows/export_strings.yml), and use a different matching criterion:
* `nofile` will copy translations if the ID and source text match, ignoring the file. This is useful to minimize the impact of code refactoring.
* `matchid` will ignore both file and source text, copying translations if the ID matches. This is useful for source changes that don’t require invalidating existing translations.

## License

Translations in this repository are available under the terms of the [Mozilla Public License v2.0](http://www.mozilla.org/MPL/2.0/).
