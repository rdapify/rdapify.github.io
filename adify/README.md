# RDAPify Admin Dashboard

**URL:** https://rdapify.com/adify

The RDAPify Admin Dashboard is a powerful management interface for administering licenses, managing users, and monitoring the platform.

## Access

### Authentication Required

- **Admin Token** — Required for all admin operations
- **Two-Factor Authentication** (2FA) — Recommended for security
- **IP Whitelisting** — Optional security layer

### Login

```
POST https://api.rdapify.com/admin/login
{
  "email": "admin@rdapify.com",
  "password": "your-password",
  "2fa_code": "123456" // if 2FA enabled
}
```

Response:
```json
{
  "session_token": "sess_xxxxx",
  "expires_at": 1710895999999
}
```

## Features

### 1. License Management

#### View Licenses
- Filter by plan (Pro, Team, Enterprise, Trial)
- Search by organization name
- View license key and expiration
- Monitor seats usage
- Check revocation status

#### Issue New Licenses
- Create licenses programmatically
- Set custom expiry dates
- Configure seat limits
- Generate trial keys (30 days)

#### Manage Licenses
- Revoke active licenses
- Extend expiration dates
- Transfer between organizations
- View audit trail

### 2. User Management

#### View Users
- List all registered users
- Filter by plan or status
- Search by email/organization
- Monitor last login date

#### Manage Accounts
- Deactivate/reactivate users
- Reset passwords
- Update billing information
- Manage 2FA settings

### 3. Analytics & Monitoring

#### Real-Time Metrics
- Active licenses count
- Monthly revenue (MRR)
- Churn rate
- Growth trends

#### Query Analytics
- Requests per day
- Average response time
- Error rates by region
- Top queried domains

#### User Activity
- Login activity
- License creation events
- API usage logs
- Security events

### 4. Webhooks & Integrations

#### Manage Webhooks
- Register webhook endpoints
- Test webhook delivery
- View delivery history
- Retry failed webhooks

#### Supported Events
- `license.created` — New license issued
- `license.revoked` — License revoked
- `license.expired` — License expired
- `subscription.updated` — Subscription changed
- `user.registered` — New user signup

### 5. Billing & Payments

#### Revenue Dashboard
- Monthly recurring revenue (MRR)
- Total customers
- Churn analysis
- Revenue trends

#### Payment Management
- View Paddle transactions
- Download invoices
- Manage refunds
- View payment failures

### 6. Security & Compliance

#### Security Audit Log
- View all admin actions
- IP address tracking
- Timestamp logging
- Change history

#### Compliance Reports
- GDPR data export requests
- Account deletion logs
- Data retention policies
- Encryption status

### 7. Bulk Operations

#### Batch Management
- Select multiple licenses at once
- Perform bulk actions (revoke, extend)
- Confirmation dialogs for safety
- Progress tracking for large batches

### 8. Advanced Filtering & Export

#### Export Data
- Export licenses, revenue, security data
- Multiple formats: JSON, CSV
- Custom date range filtering
- Scheduled report emails

### 9. Team Management

#### Admin Team
- Invite team members with role control
- Role types: Super Admin, Viewer
- Track invitations and last login
- Remove team member access instantly

### 10. API Key Management

#### Programmatic Access
- Create named API keys for automation
- Set granular permissions (read-only, read-write)
- Configure expiration (30d, 90d, 1yr, never)
- Revoke keys instantly, track usage

### 11. Automated Rules & Workflows

#### Automation Engine
- Trigger-action rules system
- Triggers: license expiring, expired, anomaly, inactive
- Actions: send email, revoke, extend
- Enable/disable rules on-the-fly

### 12. Advanced Monitoring

#### System Health
- Database statistics (row counts per table)
- API latency and request volume
- Rate limit tracking
- Active session monitoring
- Cache statistics

### 13. Security Hub

#### Advanced Threat Detection
- Failed OTP attempt logs
- IP-based suspicious activity
- Active admin session management
- Anomaly severity levels and filtering
- IP blocking functionality

### 14. Notification System

#### Multi-Channel Alerts
- Email notification toggles (created, expired, revoked, anomalies)
- Slack webhook integration
- Test notification delivery
- Customizable alert preferences

---

## User Interface

### Sidebar Navigation

```
┌──────────────────────┐
│ RDAPify Admin        │
├──────────────────────┤
│ 📊 Dashboard         │
│ 🔑 Licenses          │
│ ➕ Generate License  │
│ 💳 Billing           │
├──────────────────────┤
│ ⏳ Expiring Soon     │
│ 🛡️ Security (+logs)  │
│ 📦 Packages          │
│ ⭐ GitHub            │
├──────────────────────┤
│ 📋 Bulk Operations   │
│ 📥 Export Reports    │
│ 👥 Team Management   │
│ 🔐 API Keys          │
│ ⚙️ Automations       │
│ 🔔 Notifications     │
├──────────────────────┤
│ 💚 Health            │
│ ⚡ Quick Actions     │
├──────────────────────┤
│ 🌐 [EN / العربية]   │
└──────────────────────┘
```

### Dark Theme

- **Background**: #0b0b11
- **Sidebar**: #0f0f17
- **Cards**: #13131d
- **Accent**: #3b82f6 (Blue)
- **Text**: #e4e4e7 (Light Gray)

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `?` | Show help |
| `g h` | Go to home |
| `g l` | Go to licenses |
| `g u` | Go to users |
| `g a` | Go to analytics |
| `/ ` | Focus search |
| `Esc` | Close dialogs |

---

## API Reference

### Authentication

All API requests require a valid session token:

```bash
curl -H "Authorization: Bearer {session_token}" \
  https://api.rdapify.com/admin/licenses
```

### Endpoints

#### GET /admin/licenses

List all licenses with filters.

```bash
GET /admin/licenses?plan=pro&status=active&limit=50&offset=0
```

Parameters:
- `plan` — Filter by plan (pro, team, enterprise, trial)
- `status` — Filter by status (active, expired, revoked)
- `organization` — Search by organization name
- `limit` — Results per page (default: 50)
- `offset` — Pagination offset

#### POST /admin/licenses

Create a new license.

```bash
POST /admin/licenses
{
  "plan": "pro",
  "organization": "My Company",
  "expiry_ms": 1710895999999,
  "max_developers": 5
}
```

#### DELETE /admin/licenses/{key}

Revoke a license.

```bash
DELETE /admin/licenses/RDAP-PRO-xxxxx
```

---

## Troubleshooting

### Cannot Access Dashboard

1. Verify your admin email is registered
2. Check 2FA code (if enabled)
3. Clear browser cache and cookies
4. Try incognito/private mode
5. Contact support@rdapify.com

### License Not Appearing

1. Verify license key format: `RDAP-{PLAN}-{payload}-{signature}`
2. Check organization name matches
3. Ensure license is not expired
4. Try refreshing the page

### Webhook Not Delivering

1. Verify endpoint URL is publicly accessible
2. Check webhook signature in logs
3. Test with "Send Test Event" button
4. Review delivery history for error messages

---

## Support

- **Email**: admin-support@rdapify.com
- **Slack**: #admin-support (private)
- **Status Page**: https://status.rdapify.com
- **Documentation**: https://rdapify.com/docs/admin

---

**Last Updated:** March 23, 2026 (v2.0 — 10 new features added)
