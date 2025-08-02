name: Update README

on:
  schedule:
    - cron: "0 0 * * *"  # Runs every day at midnight
  workflow_dispatch:

jobs:
  update-readme:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repo
        uses: actions/checkout@v3
        
      - name: Update README with current date
        run: |
          echo "Last updated on $(date)" > update.txt
          git config user.name "Your Name"
          git config user.email "your-email@example.com"
          git add update.txt
          git commit -m "Auto-update on $(date '+%Y-%m-%d')"
          git push
