# `pi`

Home setup

- [`supabase`](https://supabase.com) - running as a local instance
- [`pihole`](https://pi-hole.net/) - ad blocker
- [`home-assistant`](https://www.home-assistant.io) - manage your home


## To dogfood

- Local AI stack: https://github.com/ykhli/local-ai-stack
  - currently cannot run local model - too large
 
## Usage

Make sure you have docker-compose installed on your Pi (`sudo apt-get install -y docker-compose`). You might need to give elevated access then restart your Pi (`sudo usermod -aG docker $USER`)

- `cp .env.example .env` - change all values
- `docker-compose up -d` 
