---
title: "Flutter and the pubspec file"
description: "Describes the Flutter-only fields in the pubspec file."
---

{{site.alert.note}}
  This page is primarily aimed at folks who write
  Flutter apps. If you write packages or plugins, 
  (perhaps you want to create a federated plugin),
  you should check out the
  [Developing packages and plugins][] page.
{{site.alert.end}}

Every Flutter project includes a `pubspec.yaml` file,
often referred to as _the pubspec_.
A basic pubspec is generated when you create
a new Flutter project. It's located at the top
of the project tree and contains metadata about
the project that the Dart and Flutter tooling
needs to know. The pubspec is written in
[YAML][], which is human readable, but be aware
that _white space (tabs v spaces) matters_.

[YAML]: https://yaml.org/

The pubspec file specifies dependencies
that the project requires, such as particular packages
(and their versions), fonts, or image files.
It also specifies other requirements, such as 
dependencies on developer packages (like
testing or mocking packages), or particular
constraints on the version of the Flutter SDK. 

Fields common to both Dart and Flutter projects
are described in [the pubspec file][] on [dart.dev][].
This page lists _Flutter-specific_ fields
that are only valid for a Flutter project.

{{site.alert.note}}
  The first time you build your project, it
  creates a `pubspec.lock` file that contains
  specific versions of the included packages.
  This ensures that you get the same version
  the next time the project is built.
{{site.alert.end}}

[the pubspec file]: {{site.dart-site}}/tools/pub/pubspec
[dart.dev]: {{site.dart-site}}

When you create a new project with the
`flutter create` command (or by using the
equivalent button in your IDE), it creates
a pubspec for a basic Flutter app.

Here is an example of a Flutter project pubspec file.
The Flutter only fields are highlighted.

{% prettify yaml %}
name: <project name>
description: A new Flutter project.

publish_to: none

version: 1.0.0+1

environment:
  sdk: '>=3.2.0 <4.0.0'

dependencies:
  [[highlight]]flutter:[[/highlight]]       # Required for every Flutter project
    [[highlight]]sdk: flutter[[/highlight]] # Required for every Flutter project
  [[highlight]]flutter_localizations:[[/highlight]] # Required to enable localization
    [[highlight]]sdk: flutter[[/highlight]]         # Required to enable localization

  [[highlight]]cupertino_icons: ^1.0.6[[/highlight]] # Only required if you use Cupertino (iOS style) icons

dev_dependencies:
  [[highlight]]flutter_test:[[/highlight]]
    [[highlight]]sdk: flutter[[/highlight]] # Required for a Flutter project that includes tests

  [[highlight]]flutter_lints: ^3.0.0[[/highlight]] # Contains a set of recommended lints for Flutter code

[[highlight]]flutter:[[/highlight]]

  [[highlight]]uses-material-design: true[[/highlight]] # Required if you use the Material icon font

  [[highlight]]generate: true[[/highlight]] # Enables generation of localized strings from arb files

  [[highlight]]assets:[[/highlight]]  # Lists assets, such as image files
    [[highlight]]- images/a_dot_burr.jpeg[[/highlight]]
    [[highlight]]- images/a_dot_ham.jpeg[[/highlight]]

  [[highlight]]fonts:[[/highlight]]              # Required if your app uses custom fonts
    [[highlight]]- family: Schyler[[/highlight]]
      [[highlight]]fonts:[[/highlight]]
        [[highlight]]- asset: fonts/Schyler-Regular.ttf[[/highlight]]
        [[highlight]]- asset: fonts/Schyler-Italic.ttf[[/highlight]]
          [[highlight]]style: italic[[/highlight]]
    [[highlight]]- family: Trajan Pro[[/highlight]]
      [[highlight]]fonts:[[/highlight]]
        [[highlight]]- asset: fonts/TrajanPro.ttf[[/highlight]]
        [[highlight]]- asset: fonts/TrajanPro_Bold.ttf[[/highlight]]
          [[highlight]]weight: 700[[/highlight]]
{% endprettify %}
 
## Assets

Common types of assets include static data
(for example, JSON files), configuration files,
icons, and images (JPEG, WebP, GIF,
animated WebP/GIF, PNG, BMP, and WBMP).

Besides listing the images that are included in the
app package, an image asset can also refer to one or more
resolution-specific "variants". For more information,
see the [resolution aware][] section of the
[Assets and images][] page.
For information on adding assets from package
dependencies, see the
[asset images in package dependencies][]
section in the same page.

[Assets and images]: {{site.url}}/ui/assets/assets-and-images
[asset images in package dependencies]: {{site.url}}/ui/assets/assets-and-images#from-packages
[resolution aware]: {{site.url}}/ui/assets/assets-and-images#resolution-aware

## Fonts

As shown in the above example,
each entry in the fonts section should have a
`family` key with the font family name,
and a `fonts` key with a list specifying the
asset and other descriptors for the font.

For examples of using fonts
see the [Use a custom font][] and
[Export fonts from a package][] recipes in the
[Flutter cookbook][].

[Export fonts from a package]: {{site.url}}/cookbook/design/package-fonts
[Flutter cookbook]: {{site.url}}/cookbook
[Use a custom font]: {{site.url}}/cookbook/design/fonts

## More information

For more information on packages, plugins,
and pubspec files, see the following:

* [Creating packages][] on dart.dev
* [Glossary of package terms][] on dart.dev
* [Package dependencies][] on dart.dev
* [Using packages][]
* [What not to commit][] on dart.dev

[Creating packages]: {{site.dart-site}}/guides/libraries/create-library-packages
[Developing packages and plugins]: {{site.url}}/packages-and-plugins/developing-packages
[Federated plugins]: {{site.url}}/packages-and-plugins/developing-packages#federated-plugins
[Glossary of package terms]: {{site.dart-site}}/tools/pub/glossary
[Package dependencies]: {{site.dart-site}}/tools/pub/dependencies
[Using packages]: {{site.url}}/packages-and-plugins/using-packages
[What not to commit]: {{site.dart-site}}/guides/libraries/private-files#pubspeclock
