# Lab 52 — Network File Transfers (wget/curl)

## 📌 Overview

Linux provides command-line utilities for retrieving resources from network services.

This lab introduces two widely used tools:

- `wget`
- `curl`

You will learn their basic usage for network file transfers and HTTP-based communication.

---

## 🎯 Objective

By completing this lab, you will learn how to:

- Understand command-line network transfers
- Use `wget` to download files
- Use `curl` to retrieve resources
- Inspect HTTP responses
- Save downloaded content
- Understand practical uses of `wget` and `curl`

---

## 📚 Prerequisites

You should have:

- Basic Linux command-line knowledge
- Internet connectivity
- Familiarity with files and directories
- Basic understanding of URLs

---

## 🧠 Introduction

`wget` and `curl` are command-line networking utilities.

### wget

`wget` is commonly used to download files from network resources.

```bash
wget https://example.com/
```

### curl

`curl` can transfer data using many network protocols and is commonly used for HTTP requests.

```bash
curl https://example.com/
```

---

## 🌐 Using wget

Check whether `wget` is installed:

```bash
wget --version
```

Download a resource:

```bash
wget https://example.com/
```

Save a resource using a specified filename:

```bash
wget -O example.html https://example.com/
```

List the downloaded file:

```bash
ls -lh example.html
```

---

## 🌐 Using curl

Check the installed version:

```bash
curl --version
```

Retrieve a webpage:

```bash
curl https://example.com/
```

Save the response to a file:

```bash
curl -o example.html https://example.com/
```

---

## 📡 Inspect HTTP Headers

Use:

```bash
curl -I https://example.com/
```

This displays HTTP response headers.

Headers can provide information about:

- HTTP status
- Content type
- Server behavior
- Caching
- Redirects

---

## 🔄 Follow Redirects

Use:

```bash
curl -L https://example.com/
```

The `-L` option follows HTTP redirects.

---

## 🧪 Practical Lab

### Task 1 — Test wget

```bash
wget --version
```

### Task 2 — Test curl

```bash
curl --version
```

### Task 3 — Retrieve a webpage

```bash
curl https://example.com/
```

### Task 4 — Save the webpage

```bash
curl -o example.html https://example.com/
```

### Task 5 — Download using wget

```bash
wget -O example-wget.html https://example.com/
```

### Task 6 — Inspect HTTP headers

```bash
curl -I https://example.com/
```

### Task 7 — Compare the downloaded files

```bash
ls -lh example.html example-wget.html
```

---

## 🔎 Command Reference

| Command | Purpose |
|---|---|
| `wget URL` | Download a resource |
| `wget -O file URL` | Save using a specified filename |
| `curl URL` | Retrieve a resource |
| `curl -o file URL` | Save output to a file |
| `curl -I URL` | Display HTTP headers |
| `curl -L URL` | Follow redirects |

---

## 🧠 Key Concepts

- `wget` is commonly used for downloading resources.
- `curl` is a flexible data-transfer utility.
- HTTP headers provide information about a response.
- Redirects can be followed with `curl -L`.
- Both utilities are useful in Linux administration and automation.

---

## 🛡️ Security Perspective

`curl` and `wget` are frequently used by system administrators and security professionals.

They can help with:

- Testing web servers
- Inspecting HTTP responses
- Troubleshooting connectivity
- Downloading trusted software
- Testing APIs
- Investigating network behavior

Only download files from sources you trust.

---

## ⚠️ Best Practices

- Verify URLs before downloading.
- Avoid executing downloaded scripts without reviewing them.
- Use HTTPS whenever available.
- Be cautious with files obtained from unknown sources.
- Consider verifying checksums for important downloads.

---

## 📝 Questions

1. What is `wget` commonly used for?
2. What is `curl` commonly used for?
3. What does `curl -I` display?
4. What does `curl -L` do?
5. Why should downloaded files be treated carefully?
6. Why is HTTPS preferred?

---

## 🧹 Cleanup

```bash
rm -f example.html example-wget.html
```

---

## 📋 Lab Completion Checklist

- [ ] Verify wget
- [ ] Verify curl
- [ ] Download a resource
- [ ] Save curl output
- [ ] Inspect HTTP headers
- [ ] Follow redirects
- [ ] Understand safe downloading practices

---

## 📌 Summary

In this lab, you learned how to use `wget` and `curl` for basic network file transfers and HTTP inspection.

These utilities are essential tools for Linux administration, troubleshooting, automation, and security work.

---

## 🚀 Next Lab

**Lab 53 — Checking System Uptime**
