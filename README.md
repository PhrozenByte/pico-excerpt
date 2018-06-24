Pico Excerpt
============

This is the repository of Pico's official `PicoExcerpt` plugin.

Pico is a stupidly simple, blazing fast, flat file CMS. See http://picocms.org/ for more info.

**This plugin exists for historic reasons only and should not be used!**

`PicoExcerpt` is a simple plugin that creates excperts of all your pages and makes them available using `{{ page.excerpt }}`. Installing this plugin is **highly discouraged**, because it depends on Pico's official [`PicoParsePagesContent` plugin][PicoParsePagesContent], that has a significant negative impact on your website's performance.

The main reason Pico started parsing the Markdown contents of all pages (see `PicoParsePagesContent`), was the desire for automatically generated page excerpts. We later realized that this is the wrong approach and started searching for alternatives - and we think we found a better solution. We recommend to part from the concept of automatically generated excerpts. Instead, you should use the `Description` meta header to write excerpts on your own. Starting with Pico 1.0 you can use `%meta.*%` placeholders in your Markdown files, so you don't have to repeat yourself - simply add `%meta.description%` to the page content and Pico will replace it with your excerpt.

By popular request we removed parsing the Markdown contents of all pages with Pico 1.0. This significantly improved Pico's performance. To preserve backwards compatibility (BC) we introduced the `PicoParsePagesContent` and `PicoExcerpt` plugins. Both plugins have been removed from Pico's default installation with Pico 2.0, but you can still install them manually.

Install
-------

If you're using a `composer`-based installation of Pico (e.g. [`picocms/pico-composer`][PicoComposer]), simply open a shell on your server, navigate to Pico's install directory (e.g. `/var/www/html`) and run `composer require phrozenbyte/pico-excerpt` (via [Packagist.org][]). That's it!

If you're rather using one of [Pico's pre-built release packages][PicoRelease], you must install the [`PicoParsePagesContent` plugin][PicoParsePagesContent] first. After you've installed `PicoParsePagesContent`, create a empty `plugins/PicoExcerpt` directory in Pico's install directory (e.g. `/var/www/html`) on your server. Then download [`PicoExcerpt`'s latest source package][PicoPluginRelease] and upload all containing files (esp. `PicoExcerpt.php`) into said `plugins/PicoExcerpt` directory (resulting in `plugins/PicoExcerpt/PicoExcerpt.php`).

`PicoExcerpt` requires Pico 1.0+

Config
------

`PicoExcerpt` is disabled by default due to the significant negative performance impact of the required `PicoParsePagesContent` plugin. You can enable the plugin by adding the following to your `config/config.yml`:

```yml
PicoExcerpt.enabled: true
```

`PicoExcerpt` itself has no config options.

[PicoComposer]: https://github.com/picocms/pico-composer
[Packagist.org]: https://packagist.org/packages/phrozenbyte/pico-excerpt
[PicoRelease]: https://github.com/picocms/Pico/releases/latest
[PicoPluginRelease]: https://github.com/PhrozenByte/pico-excerpt/releases/latest
[PicoParsePagesContent]: https://github.com/PhrozenByte/pico-parse-pages-content
