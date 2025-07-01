# 🔒   Actions Secret Leak Vulnerability Demo

⚠️ **WARNING**: This repository demonstrates a **SECURITY VULNERABILITY**. Do not use these patterns in production!

## 🎯 Purpose

This repository demonstrates why **base64 encoding secrets in GitHub Actions is NOT secure** and how it can lead to secret exposure.

## 🚨 The Vulnerability

Many developers mistakenly believe that base64 encoding provides security for secrets. **This is incorrect!**

### ❌ Vulnerable Pattern:
```yaml
- name: "Insecure Secret Handling"
  run: |
    ENCODED_SECRET=$(echo "${{ secrets.API_KEY }}" | base64)
    echo "Encoded secret: $ENCODED_SECRET"
```

### 🔍 Why This Is Dangerous:

1. **Base64 is encoding, not encryption** - no key required to decode
2. **GitHub Actions logs are visible** to repository collaborators
3. **Anyone can decode base64** using simple commands or online tools
4. **Secrets become permanently exposed** in workflow logs

### 🔐 Best Practices:

1. **Never print or echo secrets** in workflow logs
2. **Use secrets directly** in secure operations
3. **Leverage environment variables** for passing secrets to applications
4. **Use proper secret management** tools and services
5. **Regularly rotate secrets** and monitor for exposure

## 📋 Demo Workflow

The workflow in `.github/workflows/vulnerable-workflow.yml` demonstrates:

- ❌ How base64 encoding exposes secrets
- ❌ Common vulnerable patterns developers use

## ⚖️ Responsible Disclosure

This repository is for **educational purposes only**. If you discover similar vulnerabilities in production systems:

1. **Do not exploit** the vulnerability
2. **Report responsibly** to the organization
3. **Follow responsible disclosure** practices
4. **Help improve security** for everyone

---

**Remember**: Security is everyone's responsibility. Learn these patterns to protect, not to exploit! 🛡️
