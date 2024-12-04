# Cloud Run Domain Mapping Guide

Add CNAME record in GoDaddy:
- Type: CNAME
- Host: disc-assessment
- Points to: ghs.googlehosted.com
- TTL: 600

Configure Cloud Run mapping:
```bash
gcloud run domain-mappings create --service disc-assessment --domain YOUR_DOMAIN --region us-central1
```

Verify setup:
```bash
gcloud run domain-mappings list --platform managed --region us-central1
```