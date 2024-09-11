name: Update README

on:
  schedule:
    - cron: '0 0 * * *'  # Runs daily at midnight
  workflow_dispatch:

jobs:
  update-readme:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Generate README content
        id: generate_readme
        run: |
          #!/bin/bash
          # Define your GitHub username
          USERNAME="Momwhyareyouhere"
          
          # Fetch user data
          USER_DATA=$(curl -s https://api.github.com/users/$USERNAME)
          REPOS_DATA=$(curl -s https://api.github.com/users/$USERNAME/repos?per_page=100)

          # Parse JSON data
          NAME=$(echo "$USER_DATA" | jq -r '.name')
          PUBLIC_REPOS=$(echo "$USER_DATA" | jq -r '.public_repos')
          FOLLOWERS=$(echo "$USER_DATA" | jq -r '.followers')
          FOLLOWING=$(echo "$USER_DATA" | jq -r '.following')
          AVATAR_URL=$(echo "$USER_DATA" | jq -r '.avatar_url')

          # Generate language stats
          LANGUAGES=$(echo "$REPOS_DATA" | jq -r '.[].languages_url' | xargs -I {} curl -s {} | jq -r 'to_entries[] | "\(.key): \(.value)"' | sort | uniq -c | sort -nr | awk '{print "- " $2 ": " $1}')

          # Write to README.md
          cat > README.md << EOL
          # Hello 👋

          ![Avatar]($AVATAR_URL)
          ## User Stats
          - **Name**: $NAME
          - **Public Repositories**: $PUBLIC_REPOS
          - **Followers**: $FOLLOWERS
          - **Following**: $FOLLOWING

          ## Top Languages
          $LANGUAGES
          EOL

      - name: Commit and push changes
        uses: EndBug/add-and-commit@v9
        with:
          add: 'README.md'
          message: 'Update README with GitHub stats and top languages'
          author_name: 'github-actions'
          author_email: 'github-actions@github.com'
