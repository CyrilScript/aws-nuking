## History nuking my aws account
[Source](https://github.com/rebuy-de/aws-nuke/)

   45  sudo apt-get install build-essential
   46  brew install gcc
   47  brew install aws-nuke
   48  vim nuke-config.yml
   49  aws-nuke -c nuke-config.yml --profile <ACCOUNT-ALIAS> --access-key-id <ACCESS-KEY> --secret-access-key <SECRET-KEY>

   56  aws-nuke run --config nuke-config.yml --access-key-id <ACCESS-KEY> --secret-access-key <SECRET-KEY> --no-dry-run
   57  vim nuke-config.yml
   58  aws-nuke run --config nuke-config.yml --access-key-id <ACCESS-KEY> --secret-access-key <SECRET-KEY> --no-dry-run
   59  sudo apt install awscli -y
   61  brew install awscli
   62  aws configure
   63  aws quicksight update-account-settings \\n    --aws-account-id <ACCOUNT-ID> \\n    --termination-protection-enabled false\n
   64  aws quicksight update-account-settings \\n    --aws-account-id <ACCOUNT-ID> \\n    --termination-protection-enabled false \\n    --default-namespace default\n
   65  aws quicksight update-account-settings \\n    --aws-account-id <ACCOUNT-ID> \\n    --no-termination-protection-enabled \\n    --default-namespace default\n
   66  aws-nuke run --config nuke-config.yml --access-key-id <ACCESS-KEY> --secret-access-key <SECRET-KEY> --no-dry-run
   67  export HISTTIMEFORMAT="%F %T " && history | awk -v date="$(date --date='4 hours ago' '+%F %T')" '$2" "$3 >= date' > history_last_4_hours.txt

   ----------------------

### nuke-config.yml
regions:
- us-east-1
- global

account-blocklist:
- "999999999999" # production

accounts:
  "<ACCOUNT-ID>": {}

 (where other configurations can be added)

