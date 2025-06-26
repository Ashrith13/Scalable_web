🌐 Scalable Static Website with AWS S3 + Cloudflare + GitHub Actions

This project demonstrates how to host a static website using AWS S3 and deploy it automatically with GitHub Actions. The website is secured and globally delivered using Cloudflare CDN and HTTPS.

## 🛠 Tools & Technologies Used

- **AWS S3 (Static Website Hosting)**
- **Cloudflare (DNS, CDN, SSL)**
- **GitHub Actions (CI/CD)**
- **HTML/CSS** (Static Website)
- **Bash & Git** (for automation and repo management)


## 📁 Project Structure

```

.
├── index.html
├── style.css
├── .github/
│   └── workflows/
│       └── deploy.yml
└── README.md

````
## 📌 Setup Instructions

### 1. 🧑‍💻 Clone or Fork the Repository

```bash
git clone https://github.com/Ashrith13/Scalable_web.git
cd myapp
````

---

### 2. 📝 Modify Your Website

Edit the `index.html` and `style.css` files with your own content.

---

### 3. 🪣 Create an AWS S3 Bucket

* Go to [AWS S3 Console](https://s3.console.aws.amazon.com/s3/)
* Create a new bucket with a unique name (ashrithbucket1)
* **Uncheck** “Block all public access”
* Enable **Static Website Hosting**
* Note the **Endpoint URL**

---

### 4. 🔐 Configure GitHub Secrets

In your GitHub repository, go to **Settings > Secrets > Actions** and add:

* `AWS_ACCESS_KEY_ID`
* `AWS_SECRET_ACCESS_KEY`

---

### 5. ⚙️ GitHub Actions Workflow

Create `.github/workflows/deploy.yml` with the following:

```yaml
name: Deploy to S3
on:
  push:
    branches:
      - main
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Sync to S3
        uses: jakejarvis/s3-sync-action@master
        with:
          args: --delete
        env:
          AWS_S3_BUCKET: ashrithbucket1
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          AWS_REGION: ap-south-1
```

Push your code to GitHub — your site will auto-deploy!

---

### 6. 🌐 Connect Cloudflare (Optional but Recommended)

* Create an account at [Cloudflare](https://cloudflare.com)
* Add your custom domain and update nameservers
* Point domain to S3 endpoint
* Enable **SSL/TLS**, **Always use HTTPS**, and **Caching**


This project is free to use for educational purposes.

```

---

Let me know if you’d like help generating the `deploy.yml` file or uploading screenshots to complete the README.
```
