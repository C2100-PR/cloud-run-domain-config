# Cloud Run Domain Mapping Guide

## GoDaddy DNS Configuration

### Required DNS Records

1. Create a CNAME record:
   - Type: CNAME
   - Host/Name: disc-assessment (or @ for root domain)
   - Points to: ghs.googlehosted.com
   - TTL: 600 seconds (or 1 hour)

### Verification Steps

1. Login to GoDaddy DNS management
2. Navigate to DNS Management section
3. Add new record with above settings
4. Save changes

## Cloud Run Configuration

### Domain Mapping Command
```bash
gcloud run domain-mappings create \
  --service disc-assessment \
  --domain YOUR_DOMAIN \
  --region us-central1 \
  --platform managed
```

### Verification Steps

1. Wait for SSL certificate provisioning (can take up to 24 hours)
2. Verify mapping status:
```bash
gcloud run domain-mappings list \
  --platform managed \
  --region us-central1
```

## Troubleshooting

### Common Issues
1. DNS propagation can take up to 48 hours
2. SSL certificate provisioning may require additional verification
3. Domain ownership verification might be needed in Google Cloud Console

### Verification Commands
```bash
# Check domain mapping status
gcloud run domain-mappings describe \
  --domain YOUR_DOMAIN \
  --platform managed \
  --region us-central1

# Verify DNS resolution
dig YOUR_DOMAIN
```