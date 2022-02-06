# ggd-son-availability-pub
Some of the SON locations have started helping out the GGD with COVID testing. This repo contains timeslot availability data as scraped and anonymized from the https://www.coronatestafspraak.nl/ API.

## Description
All anonymized timeslots and location data is located in the [data/](data/) folder.

### [latest-locations.csv](data/latest-locations.csv)
* `name` anonymized id of the location. This field is anonymized because the API seems to use an internal UUID for this.
* `test_type` anonymized test-type used by the location. This field is anonymized because the API seems to use an internal UUID for this. At the moment of writing only `animato-photon` seems to be in use. Although I can't be certain I'm fairly certain that this is a test of the type rapid lateral flow.  
* `test_provider_id` anonymized id of the test-provider. This field is anonymized because the API seems to use an internal UUID for this. This id seems to be unique on an organisation level as registered by the GGD. It seems that one `test_provider_id` can hold multiple `name`-ID's.
* `postal_code` postal code of the location without the letters.
* `city` city of the location.
* `active` this field seems to indicate if the location still participates or not.
* `location_name` the name of the location. This seems to be related to `test_provider_id`.

### [latest-timeslots.csv](data/latest-timeslots.csv)
Available timeslots as scanned for today. While the reservation system allows booking multiple days in advance, the scraper only scrapes slots available today.

* `SampleTime` time when the sample was taken. This is the timestamp of the scraper script and it denotes at what timestamp that specific sample was taken from the API.
* `startTimeslot` this describes the timeslots starting time. At the time of writing timeslots seem to be divided in 15-min chunks. Each row in the file describes the availability for 15 minutes starting at `startTimeslot`.
* `maximumCapacity` the maximum available capacity at that timeslot for this location.
* `bookings` this seems to be the number of bookings made for this location on this specific timeslot.
* `availableCapacity` this seems to denote the maximum capacity for this location on this specific timeslot.
* `hasAvailability` this seems to denote if a location is available on this specific timeslot.
* `location_id` this maps to `name` in [latest-locations.csv](data/latest-locations.csv).
* `postal_code` the postal code of the location.
* `city` the city of the location.
* `active` this field seems to indicate if the location still participates or not.

### Additional csv files
There are additional timestamped files available in the [data/](data/) folder. These files contain what is described in the above chapters but for a specific day. This allows one to easily look up historical data.

## License
The anonymized data is licensed CC0. The original data is copyright [https://www.coronatestafspraak.nl/](https://www.coronatestafspraak.nl/).

Please cite: `Phil, T. (2022). Sikerdebaard/ggd-son-availability-pub. GitHub Repository. Retrieved Month Day, Year, from https://github.com/Sikerdebaard/ggd-son-availability-pub`
