# 🔒 Actions Secret Leak Vulnerability Demo

⚠️ **WARNING**: This repository demonstrates a **SECURITY VULNERABILITY**. Do not use these patterns in production!

## 🎯 Purpose

This repository demonstrates why **anyone with write access to your repository can expose secrets** by modifying workflows, even with GitHub's encrypted secrets.

## 🚨 The Core Issue

**Repository write access = potential secret access.** Anyone who can edit workflow files can extract secret values using simple techniques like base64 encoding.

### ❌ Vulnerable Pattern:
```yaml
- name: "Secret Exposure"
  run: |
    # Anyone with write access can add this
    echo "${{ secrets.API_KEY }}" | base64
    # Output: ZG9uZ3RyYW4K (easily decoded to: dongtran)
```

### 🔍 Why This Matters:
- Base64 bypasses GitHub's secret masking in logs
- Anyone can decode base64 to get the original secret
- Workflow logs are visible to repository collaborators  
- Write access essentially means secret access

## 🛡️ Best Practices:

1. **Limit write access** to trusted team members only
2. **Use branch protection** with required reviews for workflow changes
3. **Never print/echo secrets** in workflow logs
4. **Consider external secret management** for sensitive environments
5. **Regular access audits** of repository permissions

## 📋 Demo Workflow

The workflow demonstrates:
- ❌ How easily secrets can be exposed via base64
- ❌ Common vulnerable patterns developers use

## ⚖️ Responsible Usage

This repository is for **educational purposes only**:

1. **Use this knowledge to improve security** in your projects
2. **Implement proper access controls** before storing secrets
3. **Never exploit** these techniques maliciously

---

**Remember**: The best defense is limiting who can modify your workflows! 🛡️