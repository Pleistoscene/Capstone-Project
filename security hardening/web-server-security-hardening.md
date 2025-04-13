# RAHJ.ca Web Server – Security Hardening Documentation
This document details all security measures implemented on the [RAHJ.ca](https://rahj.ca) production web server to ensure confidentiality, integrity, and availability of services.

## 1. SSL/TLS & HTTPS Setup
- Enabled HTTPS using **Let’s Encrypt SSL certificate**:
  - `fullchain.pem` and `privkey.pem` installed via Certbot.
- Configured Apache to listen on port 443.
- Forced HTTPS redirection from HTTP using:
  
  **`/etc/apache2/sites-available/000-default.conf`**
  ```apache
  <VirtualHost *:80>
      ServerName rahj.ca
      ServerAlias www.rahj.ca
      Redirect permanent / https://rahj.ca/
  </VirtualHost>
  ```

## 2. Apache Security Headers
Set security headers inside the HTTPS virtual host to mitigate common web threats.

**`/etc/apache2/sites-available/rahj-ssl.conf`**
```apache
<IfModule mod_headers.c>
    Header always set X-Frame-Options "SAMEORIGIN"
    Header always set X-Content-Type-Options "nosniff"
    Header always set Referrer-Policy "strict-origin-when-cross-origin"
    Header always set Permissions-Policy "geolocation=(), microphone=(), camera=()"
    Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains"
</IfModule>
```

**Purpose of Headers:**
| Header                        | Purpose |
|------------------------------|---------|
| `X-Frame-Options`            | Prevents clickjacking |
| `X-Content-Type-Options`     | Stops MIME-type sniffing |
| `Referrer-Policy`            | Controls referral leakage |
| `Permissions-Policy`         | Blocks camera, mic, location abuse |
| `Strict-Transport-Security`  | Forces HTTPS and resists downgrade attacks |

## 🛡3. Fail2Ban – Brute Force Protection
Installed and configured **Fail2Ban** to block SSH brute-force attempts.

### Installed via:
```bash
sudo apt install fail2ban -y
```

### Config: **`/etc/fail2ban/jail.local`**
```ini
[sshd]
enabled = true
port    = ssh
logpath = %(sshd_log)s
backend = systemd
maxretry = 5
bantime  = 600
findtime = 600
```

### Commands Used:
```bash
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
sudo fail2ban-client status sshd
```

- Bans IPs after 5 failed login attempts within 10 minutes
- Automatically unbans after 10 minutes

## 4. UFW (Uncomplicated Firewall)

Used UFW to restrict network-level access and allow only required ports.

```bash
sudo ufw allow OpenSSH
sudo ufw allow 'Apache Full'
sudo ufw enable
```

### Current Rules:
| Service       | Port(s)    | Status             |
|---------------|------------|--------------------|
| SSH           | 22         | Allowed            |
| Apache (HTTP) | 80         | Allowed            |
| Apache (HTTPS)| 443        | Allowed            |
| All Others    | —          | Blocked by default |

Checked with:
```bash
sudo ufw status verbose
```

## 5. Contact Page
- Static `/contact` page — **no form**, no backend handler.
- Displays contact email only (using `mailto:`).
- No risk of spam, injection, or abuse — no reCAPTCHA needed.

## 6. Verification Results
### curl check:
```bash
curl -I https://rahj.ca
```

Expected headers confirmed:
- `X-Frame-Options: SAMEORIGIN`
- `X-Content-Type-Options: nosniff`
- `Referrer-Policy: strict-origin-when-cross-origin`
- `Permissions-Policy: ...`
- `Strict-Transport-Security: ...`

### Online Scan Results:
| Tool                                                          | Result  |
|---------------------------------------------------------------|---------|
| [securityheaders.com](https://securityheaders.com)            | A+      |
| [observatory.mozilla.org](https://observatory.mozilla.org)    | Secure  |
| SSL Test (Qualys)                                             | Grade A |

## Summary
| Component        | Status               |
|------------------|----------------------|
| SSL/TLS          | Enabled              |
| HTTPS Redirect   | Permanent            |
| Security Headers | Fully Applied        |
| Firewall (UFW)   | Active               |
| SSH Protection   | Fail2Ban Enforced    |
| Contact Page     | Static, no spam risk |

Maintained by: `SRV-01`  
Server: Ubuntu 24.04 LTS  
Web Server: Apache 2.4.58  
Domain: [https://rahj.ca](https://rahj.ca)
