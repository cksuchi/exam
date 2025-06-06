on:
  push:
    branches: [ main ]

name: CI/CD Pipeline

jobs:
  build_and_test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 18

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test

      - name: Deploy
        if: github.ref == 'refs/heads/main' # Deploy only on main branch
        run: echo "Deploying to production" # Replace with your actual deployment command
