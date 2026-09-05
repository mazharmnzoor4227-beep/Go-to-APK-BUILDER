# Code2APK Free

This project is a **real HTML/CSS/JS → Android APK builder** designed for personal use with no paid build API.

## What it does
1. Paste a complete HTML app, or upload a ZIP that contains `index.html`.
2. Enter App Name and Package ID.
3. Upload an app icon.
4. Press **GENERATE APK**.
5. The web app uploads a build job to your GitHub repository.
6. GitHub Actions creates a trusted Capacitor Android project and runs Gradle.
7. The generated `.apk` is returned as a GitHub Actions artifact.

The APK is not a renamed HTML/ZIP file. It is built by the Android Gradle build process.

## One-time setup

### 1. Create a GitHub repository
Create a repository such as:
`code2apk-builder`

Put all files from this ZIP into that repository and make sure the default branch is `main`.

The repository must contain:
`.github/workflows/build-apk.yml`

### 2. Create a fine-grained GitHub token
For your own repository, create a fine-grained token that has access only to the Code2APK repository.

Required repository permissions:
- Contents: Read and write
- Actions: Read and write
- Metadata: Read

Do not share this token. Code2APK stores it only in your own browser's localStorage.

### 3. Host the builder UI for free
You can host `index.html` on GitHub Pages, or open it from a normal static host.

For GitHub Pages:
- Repository Settings
- Pages
- Deploy from branch
- main / root

Then open the Pages URL.

### 4. Use the app
Enter:
- GitHub username/owner
- repository name
- token
- your app's HTML/ZIP
- app name
- package id (or allow the UI to generate one)
- icon

Then press **GENERATE APK**.

## Important
This first version intentionally accepts static web apps (HTML/CSS/JavaScript/assets). It does not execute user-provided npm/Gradle/shell scripts.

Uploaded job ZIPs are committed under `jobs/` in your repository. Delete old job files occasionally.

## Free limits
GitHub documents that standard GitHub-hosted Actions runners are free for public repositories. GitHub Free private repositories have an included monthly minutes allowance. Artifact storage also has plan limits.

## Security
Use a repository-specific fine-grained token. Never use a token with access to all of your repositories.

## Android icon
For best results upload a square PNG/JPG, ideally at least 1024×1024. The workflow uses Capacitor's asset generator.

## Output
The downloaded GitHub artifact is a ZIP containing the real `.apk` file.
