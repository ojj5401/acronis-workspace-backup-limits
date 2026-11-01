# acronis google workspace backup: what it actually covers, the limits buried in official docs, and how to get it starting at $4/month

Most people searching for Acronis Google Workspace backup want two things: proof that Google isn't already backing up their company data properly, and a concrete price for fixing that. Short version: Google's native tools (Vault, Takeout, the data region policy) handle compliance and service availability, not point-in-time recovery. Acronis covers Gmail, Drive including Team Drives, Calendar, and Contacts with cloud-to-cloud backup that includes unlimited cloud storage in its Workspace licensing — and through Sharktech, you can get Acronis-powered backup hosting with 200 GB of cloud storage from **$4/month**, no long-term contracts.

> **Quick take:** If you run a small team on Google Workspace and want automated, restorable backups without paying per-seat enterprise pricing, Sharktech's Acronis backup service is the lowest entry point we found: $4/month for 200 GB on monthly billing. Configure your capacity in their portal before checkout — the final price depends on the options you pick. 👉 [See Sharktech's Acronis backup plans starting at $4/month](https://bit.ly/SharKtech)

## Why Google Workspace still needs a third-party backup

Google keeps your data available, but that's a different job from backing it up. Google's own data region policy only covers data at rest for disaster recovery and business continuity. Data in transit and data in use are your responsibility, and Google says as much in its own documentation.

The built-in tools have specific gaps:

- **Google Vault** archives specific apps for compliance and legal hold. It doesn't guarantee point-in-time recovery, and it won't save you from an admin accidentally deleting a user's Drive.
- **Google Takeout** is a manual export. Nobody runs a manual export daily, and restoring from a Takeout archive is its own project.
- Retention periods are limited, search across backups is limited, and there's no monitoring that tells you a backup failed at 2 AM.

Then there's the security angle. In April 2023, a zero-day vulnerability called GhostToken let attackers compromise Google accounts, with Google Workspace accounts potentially in the blast radius. And Acronis's threat reporting recorded a 62% spike in ransomware activity in March 2023 versus the monthly average. When the platform itself has a bad month, the only real answer is a recovery point stored somewhere else — which is exactly what cloud-to-cloud backup gives you: your Workspace data copied from Google's data centers into separate Acronis Cloud Storage, encrypted with TLS in transit and AES-256 at rest.

## What Acronis's Google Workspace backup covers

The coverage list is short because it's comprehensive for the apps that matter: Gmail mailboxes, Google Drive (including Team Drives/Shared drives), Calendar, and Contacts. The whole thing is agentless — nothing installs on your endpoints, and the backup runs from Google's infrastructure straight to Acronis cloud storage.

A few capabilities worth knowing before you buy:

- **Granular restore.** You can recover a single email, a single file, a contact, or an entire Drive. Before recovering, you can run full-text search across the backup to find the exact item — useful when an ex-employee's mailbox needs to be searched months after they left.
- **Restore from backup directly.** You can download critical files or attachments, or send emails, straight from the backup without doing a full restore first.
- **Auto-discovery.** New Workspace users and new Team Drives get detected automatically and added to your backup plans. For a growing team, this is the difference between a backup that works and one that silently misses the intern who joined last week.
- **Backup health monitoring** with reports, notifications, and alerts for failed jobs.
- **Blockchain notarization** (Acronis Notary) creates a verifiable fingerprint of backed-up Drive files — relevant if you ever need to prove a document hasn't been altered.

On licensing, Acronis states directly that its Google Workspace backup licensing includes **unlimited cloud storage, including Google Team Drive**. Keep that sentence in mind — it matters when comparing channels, because not every channel prices it that way. More on that below.

Acronis's backup-plus-security approach has held up with independent reviewers: PCMag gave Acronis Cyber Protect 17 an Editor's Choice rating of 4.5/5, citing the integrated backup and security combination.

## Sharktech's plans and pricing: the billing-cycle trap

Sharktech has partnered with Acronis for years and resells Acronis backup hosting with four billing cycles, all including 200 GB of cloud storage. This is the full set of plans currently shown on their pricing. All prices are as listed on Sharktech's official pages — capacity and add-on options are configured at checkout, so confirm the final figure in the portal before paying.

| Billing cycle | Storage included | Price | Extra storage | Buy |
| --- | --- | --- | --- | --- |
| Monthly | 200 GB | $4.00/mo | $0.02/GB | [ Order monthly backup at Sharktech](https://bit.ly/SharKtech) |
| Quarterly | 200 GB | $8.00/3 mo | $0.04/GB | [ Order quarterly backup at Sharktech](https://bit.ly/SharKtech) |
| Semi-annual | 200 GB | $12.00/6 mo | $0.06/GB | [ Order semi-annual backup at Sharktech](https://bit.ly/SharKtech) |
| Annual | 200 GB | $24.00/yr | $0.12/GB | [ Order annual backup at Sharktech](https://bit.ly/SharKtech) |

Here's the part almost nobody spells out: **the annual plan has the cheapest base price but the most expensive overage, by a factor of six.** Annual works out to $2/month equivalent, versus $4/month on monthly billing. But once your protected dataset crosses 200 GB, every extra gigabyte costs $0.12/GB on annual versus $0.02/GB on monthly. If you're backing up 350 GB, the annual plan's overage alone adds $18/month — worse than just paying the monthly plan flat out.

The decision rule:

- **Dataset confidently under 200 GB** → annual at $24/year is the cheapest real cost.
- **Dataset near or above 200 GB, or you're not sure** → monthly billing. The $0.02/GB overage is the lowest rate at any cycle, and you can switch capacity in the portal as usage grows.

File Sync & Share is an optional add-on ($0.03/GB monthly, up to $0.24/GB annual). If you don't enable it, it costs nothing — check the itemized selections before you confirm the order, because add-ons are priced separately at checkout. Sharktech's backup services carry no long-term contracts, and their technical team is reachable 24/7.

One honest caveat about scope: Sharktech's Acronis plans are metered by **storage capacity**, which suits server, VM, and device backups across Windows, Linux, and macOS. Acronis's direct Google Workspace licensing (sold through other channels) is per-workload and includes unlimited cloud storage. If Google Workspace backup is your primary goal, confirm with Sharktech's 24/7 support that the Workspace workload is included in the license tier you're configuring before you pay — it takes one chat and removes all ambiguity. 👉 [Check current Acronis backup capacity pricing at Sharktech](https://bit.ly/SharKtech)

## The hidden limits in Acronis's official docs

These come straight from Acronis's own documentation for Google Workspace protection, and they rarely make it into marketing pages:

1. **Paused and archived users get dropped after 72 hours.** They show up grayed out in the console, you can't apply new backup plans to them, and existing plans stay active for only 72 hours before removal. The backups that already exist are kept.
2. **Deleted users' backups keep billing.** When you delete a Workspace account, its existing backup isn't automatically removed — it still occupies space and is still charged. If you offboard people regularly, this line item grows unless you clean up manually.
3. **Six scheduled backups per day, maximum.** The default is once daily, and each protection plan runs at a fixed time decided by the cloud agent based on load. Manual backups are capped at 10 per hour. If you're imagining continuous protection, reset that expectation now.
4. **Shared Drives require Business Standard.** Discovering and backing up Shared Drives needs the Super Admin account to hold at least a Google Workspace Business Standard license.
5. **Dedicated Super Admin, or it breaks.** The organization must be added by a Super Admin with API access enabled. If that account is later deleted or downgraded, backups fail with "Access denied" until you re-add the organization. Acronis explicitly recommends creating a dedicated Super Admin just for backup — do it during setup, not after your first failure.
6. **Google-native files come back as Office formats.** Docs, Sheets, and Slides are backed up as .docx/.pptx-style formats and converted back on restore. Practically seamless, but if your workflow depends on exotic native formatting, test a restore early.
7. **Scale ceiling: 5,000 protected items** (mailboxes, Drives, Shared Drives) per company before performance suffers. Beyond a small enterprise's size, plan the architecture accordingly.

## How setup actually works

Because the backup is cloud-to-cloud, there's no agent to deploy on every laptop. The flow, per Acronis's guides:

1. Sign in to Google Admin as a Super Admin and enable API access (Security > API reference > Enable API access).
2. In Acronis Cyber Protect, create a personal Google Cloud project.
3. Add your Google Workspace organization, granting the service account access (this involves the JSON private key from your Google Cloud project).
4. Pick what to protect — mailboxes, Drives, Shared Drives — set the schedule and retention, and let auto-discovery handle new users from there.

Administrators need to be company admins at the customer tenant level in the Cyber Protect console; ordinary users and unit admins can't run backups or restores. If you'd rather not touch any of this yourself, Sharktech offers a free consultation and their support team assists through setup and recovery.

## How this compares on price

Pricing for Google Workspace backup varies wildly by channel and licensing model. Here are verified reference points — information only:

| Provider / channel | Model | Price |
| --- | --- | --- |
| Sharktech (Acronis hosting) | Per storage: 200 GB from $4/mo, $0.02/GB overage (monthly) | $4/mo and up |
| IDrive | Per seat: $20/seat/year, 10 TB per seat, $5/TB/mo overage | $20/seat/yr |
| CDW (Acronis Backup Advanced Google Workspace, B2B channel) | Per-seat 1-year subscription, unlimited cloud storage, agentless | Quote-based; no public per-seat price listed |
| Master Concept (Acronis, SG) | Per user, unlimited cloud backup storage | from S$5/user/mo |

The math: for a 10-person team, a per-seat model at IDrive's $20/seat/year rate runs about $200/year — roughly $1.70 per user per month. Sharktech's $4/month is $48/year for 200 GB of pooled storage, so it's cheaper if your collective data fits comfortably in that bucket. Per-seat models get attractive when you have many users with modest data each, and unlimited-storage licensing (like Acronis's direct Workspace offering through channels such as Master Concept or CDW) wins at large mailbox counts. Match the model to your shape, not to the headline number.

## Who should buy this — and who shouldn't

Sharktech's Acronis backup makes sense if you're a small business or an operator of a handful of servers and Workspace accounts who wants Acronis-grade backup infrastructure without MSP contracts, transparent pricing, and human 24/7 support.

Skip it if: your dataset is many terabytes of Workspace data (per-seat unlimited-storage licensing will cost less); you need more than 6 scheduled backups a day (no cloud-to-cloud product at this level does that, but know it going in); or you need the full Acronis security stack — advanced anti-malware and DR orchestration are license-tier dependent, and Sharktech's $4 base plan is a backup-focused configuration.

## FAQ

**Doesn't Google already back up my Workspace data?**
Only for service availability. Google's data region policy protects data at rest for disaster recovery; it doesn't give you point-in-time recovery, protection from admin error, or ransomware recovery. Vault and Takeout serve compliance and export, not operational backup.

**How often does Acronis back up Google Workspace data?**
Once daily by default, up to 6 scheduled backups per day, plus up to 10 manual backups per hour.

**What happens to backups when an employee leaves?**
Archived or suspended users stop being backed up 72 hours after their status changes. Deleted users' existing backups stay and continue to count against your storage until removed manually.

**Is there a contract?**
No. Sharktech sells backup month-to-month or longer cycles by choice, without long-term contracts.

## Before you order

Pick your billing cycle by dataset size, not by the monthly-equivalent price: under 200 GB and stable → annual at $24/year; anywhere near the limit → monthly at $4 with the $0.02/GB overage. Create the dedicated Super Admin account during setup, and test one restore in week one so you're not learning the console during an incident. If Workspace coverage in the license tier is your main question, ask support first — then 👉 [start Acronis backup from $4/month at Sharktech](https://bit.ly/SharKtech) and confirm the full price in the portal.
