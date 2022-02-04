# All in one NZB and Torrent Downloader with Streaming, VPN and Kill Switch

![image](https://user-images.githubusercontent.com/98993129/152457288-8664fdbe-0d2a-4793-8ea2-22873a843589.png)


### Description
This group of services will allow you to search and download your favourite media files. It will automatically grab the best available content and if better quality versions comes online it will grab them automatically and add them to your media folders  

---
### What's in the box?
- Gluetun (VPN Client Container)
- Transmission (Torrent Client Container)
- Prowlarr (Index and Tracker Management Container)
- Sonarr (TV Show Search and Auto Downloader)
- Radarr (Movie Search and Auto Downloader)
- Lidarr (Music Search and Auto Downloader)
- SABnzbd (Usenet file downloader)
- Homer (Dashboard for easy access to services container)
- Jellyfin (Local media streaming service container)

---

### Prerequisites
- Docker installed on host machine
- VPN Service Provider (I am currently using Mullvad) (Paid Service)
- Usenet Indexer (NZBgeek nzbgeek.info) (Paid Service)
- Usenet Provider (Newsgroup Ninja newsgroup.ninja) (Paid Service)
- Appropriate disk space (I am currently running 8tb with this setup)

---
## Instructions to get running
1. Clone this repository.
2. Update environment file `.env` with your own information, more information in the file.
3. Run `docker compose up -d` this will pull the required images and start the containers.

---

### Configure .env file
1. Update variables with your own values

---
### Setup SABnzbd
This application is used to download files from usenet groups.
1. In your browser go to SABnzb `http://localhost:8083` use the configuration that Newsgroup Ninja provided you to set up connection.

---

### Setup Prowlarr
This application is used to setup indexers and torrent trackers

####  Add your Sonarr Lidarr and Radarr applications
1. Go to Sonarr `http://localhost:8989` and grab your api key from `Settings -> General -> API Key` 
2. Go to Radarr `http://localhost:7878` and grab your api key from `Settings -> General -> API Key` 
3. Go to Lidarr `http://localhost:7878` and grab your api key from `Settings -> General -> API Key` 
4. In your browser go to Prowlarr `http://localhost:9696` 
5. Add your Sonarr Radarr and Lidarr app connections `Settings -> Apps` click the plus button under applications and click on the applications to add one by one. Your prowlarr server address is `http://localhost:9696`

#### Add your trackers and indexers to prowler
1. Watch this video to understand how to add indexers and trackers are added https://youtu.be/nPm5pMfk1OA?t=510

---

### Setup Sonarr Radarr and Lidarr download clients

#### Setup Transmission in Sonarr 
1. Go to Sonarr `http://localhost:8989`
2. Go to `Settings -> Download Clients` 
3. Click the plus button
4. Click transmission
5. Enter transmission host address `localhost`
6. Enter transmission port `9091`
7. Add a category name `movies`
8. Click test
9. Click save 

#### Setup SABnzbd in Sonarr 
1. Go to Sonarr `http://localhost:8989`
2. Go to `Settings -> Download Clients` 
3. Click the plus button
4. Click SABnzbd
5. Enter SABnzbd host address `localhost`
6. Enter SABnzbd port `8080`
6. Enter api key that you can retrieve from SABnzbd at `http://localhost:8083`
7. Add a category name `movies`
8. Click test
9. Click save 

-- Repeat above steps for Radarr and Lidarr --
