Since you're building this yourself, I recommend learning in this order: **concept → AWS setup → GitHub workflow → troubleshooting**. That sequence will make the OIDC flow much easier to understand.

## 1. Best overall (15–17 minutes)

**Authenticate GitHub Actions with AWS Using OIDC – No Secrets Needed**

[Authenticate GitHub Actions with AWS Using OIDC - No Secrets Needed](https://www.youtube.com/watch?v=Sdzd4N6L5Hg&utm_source=chatgpt.com)

**Why I recommend it**

- Uses the latest OIDC approach (no access keys)

- Explains **IAM Role**, **STS**, and **OIDC**

- Covers common errors

- Demonstrates `aws sts get-caller-identity`

- Includes the GitHub Actions YAML you'll actually use

Time: **~17 minutes**. ([YouTube](https://www.youtube.com/watch?v=Sdzd4N6L5Hg&utm_source=chatgpt.com))


## 2. Great beginner walkthrough (about 15 minutes)

**Connecting GitHub Actions to AWS Using OIDC**

[Connecting GitHub Actions To AWS Using OIDC](https://www.youtube.com/watch?v=mel6N62WZb0&utm_source=chatgpt.com)

**Why watch it**

- Straightforward explanation

- Creates the IAM role

- Connects GitHub to AWS

- Good pace if this is your first OIDC setup

([YouTube](https://www.youtube.com/watch?v=mel6N62WZb0&utm_source=chatgpt.com))


## 3. Official GitHub documentation (10–15 minutes to read)

If you prefer reading alongside the videos:

**[GitHub Docs – Configuring OpenID Connect in AWS**](https://docs.github.com/en/actions/how-tos/secure-your-work/security-harden-deployments/oidc-in-aws?utm_source=chatgpt.com)

This is the official reference for:

- Creating the OIDC provider

- Configuring the IAM trust policy

- Writing the GitHub Actions workflow

- Understanding `id-token: write` permissions ([GitHub Docs](https://docs.github.com/en/actions/how-tos/secure-your-work/security-harden-deployments/oidc-in-aws?utm_source=chatgpt.com))


## 4. AWS official explanation

**[AWS Security Blog – Use IAM Roles to Connect GitHub Actions to AWS**](https://aws.amazon.com/jp/blogs/security/use-iam-roles-to-connect-github-actions-to-actions-in-aws/?utm_source=chatgpt.com)

This explains **why** AWS recommends OIDC instead of IAM access keys and walks through the trust relationship between GitHub and AWS. ([Amazon Web Services, Inc.](https://aws.amazon.com/jp/blogs/security/use-iam-roles-to-connect-github-actions-to-actions-in-aws/?utm_source=chatgpt.com))


## 5. Excellent step-by-step blog (10–15 minutes)

**[DevOpsCube – GitHub Actions OIDC AWS Integration**](https://devopscube.com/github-actions-oidc-aws/?utm_source=chatgpt.com)

It includes:

- Architecture diagrams

- IAM Role creation

- OIDC Provider setup

- GitHub workflow examples

- Testing with `aws sts get-caller-identity` ([DevOpsCube](https://devopscube.com/github-actions-oidc-aws/?utm_source=chatgpt.com))


# The 5 concepts to understand

As you watch, focus on these ideas:

1. **GitHub OIDC Token**

   - GitHub creates a short-lived identity token for each workflow.

2. **AWS IAM Role**

   - The role your workflow assumes:

   - ```
`arn:aws:iam::866934333672:role/roc-github-connect`
```

3. **AWS STS**

   - Exchanges the GitHub OIDC token for temporary AWS credentials.

4. **Trust Policy**

   - Defines **which repository and branch** are allowed to assume the role.

5. **GitHub Actions Workflow**

   - Requests the OIDC token and uses it to authenticate to AWS.


# The OIDC flow you'll build

```
`Developer`

`      │`

`      ▼`

`git push feature-branch`

`      │`

`      ▼`

`GitHub Actions`

`      │`

`      ▼`

`GitHub issues an OIDC token`

`      │`

`      ▼`

`AWS STS verifies the token`

`      │`

`      ▼`

`IAM Role`

`roc-github-connect`

`      │`

`      ▼`

`Temporary AWS Credentials`

`      │`

`      ▼`

`Deploy to AWS`
```


# Based on your current progress

You've already accomplished:

- ✅ WSL installed and configured

- ✅ Git configured

- ✅ GitHub repository created

- ✅ GitHub CLI authentication working

- ✅ GitHub Actions workflow started

- ✅ IAM Role ARN:

- ```
`arn:aws:iam::866934333672:role/roc-github-connect`
```

You're now at the stage where understanding **OIDC** is the key remaining piece.

## My recommendation

Watch the resources in this order:

1. **Authenticate GitHub Actions with AWS Using OIDC – No Secrets Needed** (17 min) — the most up-to-date, hands-on tutorial. ([YouTube](https://www.youtube.com/watch?v=Sdzd4N6L5Hg&utm_source=chatgpt.com))

2. **Connecting GitHub Actions to AWS Using OIDC** — reinforces the setup with another practical example. ([YouTube](https://www.youtube.com/watch?v=mel6N62WZb0&utm_source=chatgpt.com))

3. Keep the official GitHub OIDC documentation open as your reference while you build. ([GitHub Docs](https://docs.github.com/en/actions/how-tos/secure-your-work/security-harden-deployments/oidc-in-aws?utm_source=chatgpt.com))

After you've watched them, I can help you build **your own production-ready GitHub Actions CI/CD pipeline** for your repository using:

- `feature-branch` → build, test, validate

- Pull Request → required review

- `main` → deploy to AWS via your `roc-github-connect` IAM role using OIDC.

