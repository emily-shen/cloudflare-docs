---
title: Store decrypted matched payloads in logs
pcx_content_type: how-to
weight: 5
---

# Store decrypted matched payloads in logs

You can include the encrypted matched payload in your [Logpush](/logs/about/) jobs by adding the **General** > [**Metadata**](/logs/reference/log-fields/zone/firewall_events/#metadata) field from the Firewall Events dataset to your job.

The payload, in its encrypted form, is available in the `encrypted_matched_data` property of the `Metadata` field.

However, you may want to decrypt the matched payload before storing the logs in your {{<glossary-tooltip term_id="SIEM">}}SIEM system{{</glossary-tooltip>}} of choice. Cloudflare provides a [sample Worker project](https://github.com/cloudflare/matched-data-worker) on GitHub that does the following:

1. Behaves as an S3-compatible storage to receive logs from Logpush. These logs will contain encrypted matched payload data.
2. Decrypts matched payload data using your private key.
3. Sends the logs to the final log storage system with decrypted payload data.

You will need to make some changes to the sample project to push the logs containing decrypted payload data to your log storage system.

Refer to the Worker project's [README](https://github.com/cloudflare/matched-data-worker/blob/main/README.md) for more information on configuring and deploying this Worker project.