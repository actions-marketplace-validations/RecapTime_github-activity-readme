# GitHub Activity in Readme

Updates a GitHub user's `README.md` with the recent GitHub activity.

<img width="735" alt="profile-repo" src="https://user-images.githubusercontent.com/25279263/87703301-3aa4a500-c7b8-11ea-8eb6-245121997a7b.png">

> **Remember that using this fork will commit your updated README as the [Recap TIme Bot](https://github.com/RecapTimeBot).**
> That account is managed by [the Pins team](https://madebythepins.tk) and will count it as an contribution to your README repo.
> If you want, add that account to your collaborators to allow us debug issues.

---

## Instructions

**NOTE**:We recommend to have an `your-username/your-username` repo on your personal GitHub account and not on your org (they're unsupported yet).

- Add the comment `<!--START_SECTION:activity-->` (entry point) within `README.md`. You can find an example
[here](https://github.com/AndreiJirohHaliliDev2006/AndreiJirohHaliliDev2006/blob/master/README.md).

- It's the time to create a workflow file called `.github/workflows/update-readme.yml`. The above job runs every half an hour, you can change it as you
wish based on the [cron syntax](https://jasonet.co/posts/scheduled-actions/#the-cron-syntax).
You can find an example [here](https://github.com/AndreiJirohHaliliDev2006/AndreiJirohHaliliDev2006/blob/master/.github/workflows/update-readme.yml).


```yml
name: Update README

on:
  schedule:
    - cron: '*/30 * * * *'

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - uses: AndreiJirohHaliliDev20067/github-activity-readme@master
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

_Inspired by [JasonEtco/activity-box](https://github.com/JasonEtco/activity-box)_
