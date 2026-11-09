# Deployment acceptance checklist
- [ ] Set a unique D1 database ID in wrangler.toml.
- [ ] Apply migrations remotely and confirm `/api/health` responds.
- [ ] Deploy Worker and verify registration/login/logout.
- [ ] Test separate accounts cannot see one another's business records.
- [ ] Test sales, credit sale, expense, product stock reduction and JSON export.
- [ ] Configure D1 backups and test restore before live use.
- [ ] Add privacy notice, account recovery, rate limiting and formal POPIA review before collecting real customer data.
