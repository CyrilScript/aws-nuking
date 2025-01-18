## History of Nuking My AWS Account

### How I Nuked My AWS Account After 5 Months of Frustration with Debit Alerts

[Source](https://github.com/rebuy-de/aws-nuke/)

1. Install necessary build tools:
   ```bash
   sudo apt-get install build-essential
   ```
2. Install GCC (via Homebrew, but an optional dependency):

   ```bash
   brew install gcc
   ```

3. Install aws-nuke (via Homebrew):

   ```bash
   brew install aws-nuke
   ```

4. Edit the `nuke-config.yml` file:

   ```bash
   vim nuke-config.yml
   ```

5. Run the actual nuke (removes resources):

   ```bash
   aws-nuke run --config nuke-config.yml --access-key-id <ACCESS-KEY> --secret-access-key <SECRET-KEY> --no-dry-run
   ```

### To Delete Quicksight Resources 

6. Install AWS CLI (if not already installed):

   ```bash
   sudo apt install awscli -y
   ```

7. Install AWS CLI via Homebrew (alternative method):

    ```bash
    brew install awscli
    ```

8. Configure AWS CLI:

    ```bash
    aws configure
    ```

9. Disable termination protection for QuickSight:

    ```bash
    aws quicksight update-account-settings --aws-account-id <ACCOUNT-ID> --no-termination-protection-enabled --default-namespace default
    ```

10. Run aws-nuke with the final configuration:

    ```bash
    aws-nuke run --config nuke-config.yml --access-key-id <ACCESS-KEY> --secret-access-key <SECRET-KEY> --no-dry-run
    ```

### `nuke-config.yml`

```yaml
regions:
  - us-east-1
  - global

account-blocklist:
  - "999999999999" # production

accounts:
  "<ACCOUNT-ID>": {}
  # (Additional configurations can be added here)
```
