# `pi`

Home setup

- [`supabase`](https://supabase.com) - running as a local instance
- [`pihole`](https://pi-hole.net/) - ad blocker
- [`home-assistant`](https://www.home-assistant.io) - manage your home

Scripts

- `rclone` - backup to Dropbox

## To dogfood

- Local AI stack: https://github.com/ykhli/local-ai-stack
  - currently cannot run local model - too large
 
## Usage

### Prereqs

Make sure you have docker-compose installed on your Pi (`sudo apt-get install -y docker-compose`). You might need to give elevated access then restart your Pi (`sudo usermod -aG docker $USER`)

### Start services

- `cp .env.example .env` - change all values
- `docker-compose up -d` 

### Access services

- pihole admin: http://localhost/admin.
  - Password: [in your .env file]
- home assistant: http://localhost:8123
