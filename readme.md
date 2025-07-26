# snk

[![GitHub release](https://img.shields.io/github/release/isitreallyalive/snk.svg?style=flat-square)](https://github.com/isitreallyalive/snk/releases/latest)
[![GitHub marketplace](https://img.shields.io/badge/marketplace-snake-blue?logo=github&style=flat-square)](https://github.com/marketplace/actions/generate-snake-game-from-github-contribution-grid)
![type definitions](https://img.shields.io/npm/types/typescript?style=flat-square)
![code style](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)

generate a snake game from a github user's contributions graph. hard fork of [platane/snk](https://github.com/platane/snk).

the project remains largely untouched and backwards compatible, but has added the following features:

- the `color_progress` options

additionally, this fork is open to contributions, so feel free to open issues or pull requests.

<picture>
  <source
    media="(prefers-color-scheme: dark)"
    srcset="https://raw.githubusercontent.com/isitreallyalive/snk/output/github-contribution-grid-snake-dark.svg"
  />
  <source
    media="(prefers-color-scheme: light)"
    srcset="https://raw.githubusercontent.com/isitreallyalive/snk/output/github-contribution-grid-snake.svg"
  />
  <img
    alt="github contribution grid snake animation"
    src="https://raw.githubusercontent.com/isitreallyalive/snk/output/github-contribution-grid-snake.svg"
  />
</picture>

pull a github user's contribution graph and turn it into a snake game. the snake eats cells in order, showing your activity.

generate a [gif](https://github.com/isitreallyalive/snk/raw/output/github-contribution-grid-snake.gif) or [svg](https://github.com/isitreallyalive/snk/raw/output/github-contribution-grid-snake.svg) image. colors can [be](https://raw.githubusercontent.com/isitreallyalive/snk/output/github-contribution-grid-snake-ocean.svg) [customized](https://raw.githubusercontent.com/isitreallyalive/snk/output/github-contribution-grid-snake-grey.svg).

available as a github action. it can automatically generate a new image each day, perfect for your [github profile readme](https://docs.github.com/en/free-pro-team@latest/github/setting-up-and-managing-your-github-profile/managing-your-profile-readme).

## usage

### github action

```yaml
- uses: isitreallyalive/snk@v3
  with:
    # github user name to read the contribution graph from (**required**)
    # using action context var `github.repository_owner` or specified user
    github_user_name: ${{ github.repository_owner }}

    # list of files to generate.
    # one file per line. each output can be customized with options as query string.

    # supported options:
    # - palette:        a preset of color, one of [github, github-dark, github-light]
    # - color_snake:    color of the snake
    # - color_dots:     comma separated list of dots color.
    #                   the first one is 0 contribution, then it goes from the low contribution to the highest.
    #                   exactly 5 colors are expected.
    # - color_progress: color of the progress bar.
    outputs: |
      dist/github-snake.svg
      dist/github-snake-dark.svg?palette=github-dark
      dist/ocean.gif?color_snake=orange&color_dots=#bfd6f6,#8dbdff,#64a1f4,#4b91f1,#3c7dd9
```

### svg

if you only want to generate an svg (not a gif), use the faster action: `isitreallyalive/snk/svg-only@v3`.

### dark mode

![dark mode](https://github.com/user-attachments/assets/6b900b64-0cdc-43f0-a234-e11dba8e786e)

for dark mode support on github, use this [special syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax#specifying-the-theme-an-image-is-shown-to) in your readme.

```html
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="github-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="github-snake.svg" />
  <img alt="github-snake" src="github-snake.svg" />
</picture>
```

### interactive demo

<a href="https://isitreallyalive.github.io/snk">
  <img height="300px" src="https://user-images.githubusercontent.com/1659820/121798244-7c86d700-cc25-11eb-8c1c-b8e65556ac0d.gif" ></img>
</a>

[isitreallyalive.github.io/snk](https://isitreallyalive.github.io/snk)

### local

```
npm install

npm run dev:demo
```
