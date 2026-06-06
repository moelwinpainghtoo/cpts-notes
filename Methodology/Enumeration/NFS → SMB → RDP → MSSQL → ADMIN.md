

```bash
## Key Insight
- NFS share expose
- NFS creds (RDP access) → SMB creds → MSSQL(local)
- MSSQL sa account disabled but creds reuse for administrator
- Always re-check leaked credentials across all services

## Attack Chain
NFS leak → SMB credentials → RDP access → credential reuse → Administrator
```