# Microsoft 365 Tenant-to-Tenant Migration Playbook

**Objective:** Provide a structured migration plan for moving users, mailboxes, and collaboration workloads from Tenant A to Tenant B during a merger, acquisition, or reorganization.

---

## 1. Discovery & Assessment
- Inventory all users, mailboxes, groups, SharePoint sites, Teams, and licenses.
- Document current tenant configurations (security, compliance, policies).
- Identify dependencies (third-party apps, line-of-business integrations).
- Assess network and bandwidth requirements.

**Artifacts to prepare:**
- User inventory spreadsheet (UPN, licenses, mailbox size).
- Application dependency map.
- Compliance and retention policy list.

---

## 2. Pre-Migration Planning
- Choose target tenant (Tenant B) and validate licensing.
- Set up identity sync (Azure AD Connect, Entra ID cross-tenant sync if applicable).
- Provision accounts and groups in Tenant B.
- Establish coexistence strategy for email (mail flow connectors, domain verification).
- Communicate timeline and expected downtime to stakeholders.

**Key Risks:**
- Email downtime during domain cutover.
- Licensing mismatches or insufficient seats.
- Duplicate usernames or conflicts.

**Mitigation:**
- Schedule migration during off-peak hours.
- Procure additional licenses ahead of migration.
- Use UPN suffixes or temporary aliases to avoid conflicts.

---

## 3. Migration Execution

### Identity
- Sync users from Tenant A to Tenant B via AD Connect or export/import CSV.
- Apply role-based access controls and conditional access policies.

### Exchange Online
- Use native M365 migration (IMAP, staged, cutover) or third-party tool (Quest, BitTitan).
- Validate mail flow and test pilot migrations before cutover.
- Update DNS MX records to point to Tenant B.

### OneDrive & SharePoint
- Use SharePoint Migration Tool (SPMT) or third-party utilities.
- Migrate shared links, permissions, and metadata.

### Teams
- Recreate Teams and channels in Tenant B.
- Export/import chat history (where supported).
- Map Teams policies and apps to new environment.

### Security & Compliance
- Reapply retention, DLP, and compliance policies in Tenant B.
- Validate conditional access rules, MFA enforcement.

---

## 4. Post-Migration Validation
- Verify mail flow, Teams chat, and file access.
- Confirm user access to all services.
- Audit license consumption and reassign if needed.
- Conduct user acceptance testing (UAT).

**Artifacts:**
- Post-migration validation checklist.
- User feedback forms.

---

## 5. Decommission & Cleanup
- Remove old connectors, domains, and licenses from Tenant A.
- Archive or export any remaining data for compliance.
- Shut down Tenant A to avoid confusion and unnecessary costs.

---

## 6. Timeline 
1. Phase 1: Discovery & Planning  
2. Phase 2: Pilot migrations & coexistence setup  
3. Phase 3: Bulk migrations (mailboxes, OneDrive, SharePoint)  
4. Phase 4: Teams migration & validation  
5. Phase 5: Cleanup & decommission  

---

**Author:** Dark👣 (Ayobamidele Adeniyi Aderosoye)  