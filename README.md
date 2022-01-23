# Visit https://github.com/lowlighter/metrics/blob/master/action.yml for full reference
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
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          # The following scopes are required:
          #  - public_access (default scope)
          # The following additional scopes may be required:
          #  - read:org  (for organization related metrics)
          #  - read:user (for user related data)
          #  - repo      (optional, if you want to include private repositories)
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: supermanas
          template: classic
          base: header, activity, community, repositories, metadata
          config_timezone: Asia/Calcutta
          plugin_habits: yes
          plugin_habits_charts: yes
          plugin_habits_days: 14
          plugin_habits_facts: yes
          plugin_habits_from: 200
          plugin_isocalendar: yes
          plugin_isocalendar_duration: half-year
          plugin_languages: yes
          plugin_languages_analysis_timeout: 15
          plugin_languages_categories: markup, programming
          plugin_languages_colors: github
          plugin_languages_limit: 8
          plugin_languages_recent_categories: markup, programming
          plugin_languages_recent_days: 14
          plugin_languages_recent_load: 300
          plugin_languages_sections: most-used
          plugin_languages_threshold: 0%
          plugin_pagespeed: yes
          plugin_pagespeed_url: .user.website
![Metrics](https://metrics.lecoq.io/supermanas?template=classic&isocalendar=1&languages=1&habits=1&pagespeed=1&isocalendar.duration=half-year&languages.limit=8&languages.sections=most-used&languages.colors=github&languages.threshold=0%25&languages.indepth=false&languages.analysis.timeout=15&languages.categories=markup%2C%20programming&languages.recent.categories=markup%2C%20programming&languages.recent.load=300&languages.recent.days=14&habits.from=200&habits.days=14&habits.facts=true&habits.charts=true&habits.trim=false&pagespeed.url=.user.website&pagespeed.detailed=false&pagespeed.screenshot=false&config.timezone=Asia%2FCalcutta)
