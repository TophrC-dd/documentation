To configure your HTTP/S Client source:

1. Select your authorization strategy.
2. Select the decoder you want to use on the HTTP messages. Logs pulled from the HTTP source must be in this format.
3. Optionally, toggle the switch to enable TLS. If you enable TLS, the following certificate and key files are required.<br>**Note**: All file paths are made relative to the configuration data directory, which is `/var/lib/observability-pipelines-worker/config/` by default. See [Advanced Configurations][10172] for more information. The file must be owned by the `observability-pipelines-worker group` and `observability-pipelines-worker` user, or at least readable by the group or user.
   - `Server Certificate Path`: The path to the certificate file that has been signed by your Certificate Authority (CA) Root File in DER or PEM (X.509) format.
   - `CA Certificate Path`: The path to the certificate file that is your Certificate Authority (CA) Root File in DER or PEM (X.509) format.
   - `Private Key Path`: The path to the `.key` private key file that belongs to your Server Certificate Path in DER or PEM (PKCS#8) format.
4. Enter the interval between scrapes.
   - Your HTTP Server must be able to handle GET requests at this interval.
   - Since requests run concurrently, if a scrape takes longer than the interval given, a new scrape is started, which can consume extra resources. Set the timeout to a value lower than the scrape interval to prevent this from happening.
5. Enter the timeout for each scrape request.

[10172]: /observability_pipelines/advanced_configurations/
<!-- 10172 link is used in multiple shortcodes, so if it is changed, make sure to update those shortcodes using find and replace -->
