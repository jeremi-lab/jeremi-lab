# Visit https://github.com/lowlighter/metrics#-documentation for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          # The following scopes are required:
          #  - public_access (default scope)
          # The following additional scopes may be required:
          #  - read:org      (for organization related metrics)
          #  - read:user     (for user related data)
          #  - read:packages (for some packages related data)
          #  - repo          (optional, if you want to include private repositories)
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: jeremi-lab
          template: terminal
          base: header, activity, community, repositories, metadata
          config_timezone: Europe/Warsaw
          plugin_achievements: yes
          plugin_achievements_display: detailed
          plugin_achievements_secrets: yes
          plugin_achievements_threshold: X
          plugin_activity: yes
          plugin_activity_days: 14
          plugin_activity_filter: all
          plugin_activity_limit: 5
          plugin_activity_load: 300
          plugin_activity_visibility: all
          plugin_habits: yes
          plugin_habits_charts_type: classic
          plugin_habits_days: 14
          plugin_habits_facts: yes
          plugin_habits_from: 200
          plugin_habits_languages_limit: 8
          plugin_habits_languages_threshold: 0%
          plugin_isocalendar: yes
          plugin_isocalendar_duration: full-year
          plugin_languages: yes
          plugin_languages_aliases: python:PY, html:HTML, css:CSS
          plugin_languages_analysis_timeout: 15
          plugin_languages_analysis_timeout_repositories: 7.5
          plugin_languages_categories: markup, programming
          plugin_languages_colors: github
          plugin_languages_ignored: javascript
          plugin_languages_limit: 8
          plugin_languages_recent_categories: markup, programming
          plugin_languages_recent_days: 14
          plugin_languages_recent_load: 300
          plugin_languages_sections: most-used
          plugin_languages_threshold: 0%
          plugin_lines: yes
          plugin_lines_history_limit: 1
          plugin_lines_repositories_limit: 4
          plugin_lines_sections: base
          plugin_people: yes
          plugin_people_limit: 24
          plugin_people_size: 28
          plugin_people_sponsors_custom: me :)
          plugin_people_thanks: me :)
          plugin_people_types: followers, following
