## History of Nuking My AWS Account

### How I Nuked My AWS Account After 5 Months of Frustration with Debit Alerts

[Source](https://github.com/rebuy-de/aws-nuke/)

1. Install necessary build tools:
   ```bash
   sudo apt-get install build-essential
   ```
2. Install GCC (via Homebrew):

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

5. Run aws-nuke with your credentials:

   ```bash
   aws-nuke -c nuke-config.yml --profile <ACCOUNT-ALIAS> --access-key-id <ACCESS-KEY> --secret-access-key <SECRET-KEY>
   ```

6. Run the actual nuke (removes resources):

   ```bash
   aws-nuke run --config nuke-config.yml --access-key-id <ACCESS-KEY> --secret-access-key <SECRET-KEY> --no-dry-run
   ```

7. Edit `nuke-config.yml` again if necessary:

   ```bash
   vim nuke-config.yml
   ```

8. Run the nuke command again (with the updated configuration):

   ```bash
   aws-nuke run --config nuke-config.yml --access-key-id <ACCESS-KEY> --secret-access-key <SECRET-KEY> --no-dry-run
   ```

9. Install AWS CLI (if not already installed):

   ```bash
   sudo apt install awscli -y
   ```

10. Install AWS CLI via Homebrew (alternative method):

    ```bash
    brew install awscli
    ```

11. Configure AWS CLI:

    ```bash
    aws configure
    ```

12. Disable termination protection for QuickSight (first attempt):

    ```bash
    aws quicksight update-account-settings --aws-account-id <ACCOUNT-ID> --termination-protection-enabled false
    ```

13. Disable termination protection for QuickSight (with default namespace):

    ```bash
    aws quicksight update-account-settings --aws-account-id <ACCOUNT-ID> --termination-protection-enabled false --default-namespace default
    ```

14. Disable termination protection for QuickSight (final attempt):

    ```bash
    aws quicksight update-account-settings --aws-account-id <ACCOUNT-ID> --no-termination-protection-enabled --default-namespace default
    ```

15. Run aws-nuke with the final configuration:

    ```bash
    aws-nuke run --config nuke-config.yml --access-key-id <ACCESS-KEY> --secret-access-key <SECRET-KEY> --no-dry-run
    ```

16. Export the last 4 hours of command history to a text file:
    ```bash
    export HISTTIMEFORMAT="%F %T " && history | awk -v date="$(date --date='4 hours ago' '+%F %T')" '$2" "$3 >= date' > history_last_4_hours.txt
    ```

---

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
