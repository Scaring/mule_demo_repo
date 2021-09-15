# Space Events API by Dmytro Kushchevyy
This is a process API that gives access to the list of Space Events and lets search event by name.
Output data is **application/json** format.

### Used external APIs:
* https://lldev.thespacedevs.com/2.2.0/event/
* https://lldev.thespacedevs.com/2.2.0/event/upcoming
* https://api.nasa.gov/planetary/apod

### Used port:
8044

### End points provided by this API:
* GET: http://localhost:{port}/api/events
    * **limit** _(default 10)_ - optional;
    * **offset** _(default 0)_ - optional;
    * **type** _from the list of events_ - optional;
    * **period** format _yyyy | yyyy-mm | yyyy-mm-dd_ - optional.
    
* GET: http://localhost:{port}/api/upcoming
    * **limit** _(default 10)_ - optional;
    * **offset** _(default 0)_ - optional.   
     
* GET: http://localhost:{port}/api/event
    * **name** - required.

*__Notice:__ if GET: http://localhost:8081/api/event?name={searched} finds more than one record than a list of available Event names is returned!*   
*__Expected type values:__* Moon Landing| Flyby| Press Event| Docking| Undocking| Landing| Launch| Rehearsal| Relocation| Release| Celestial Event| Unknown| EVA| Berthing| Static Fire| Spacecraft Event| Abort Test| Hatch Opening| Test Flight| Change of Command| Orbital Insertion| Farewell Ceremony| Ambient Pressure Test| Cryoproof Test| Wet Dress Rehearsal
    
#### Examples:
* http://localhost:{port}/api/events
```javascript
[
    {
        "id": 77,
        "name": "2017 NASA Astronaut class graduation ceremony",
        "date": "2020-01-10T15:30:00Z",
        "location": "NASA's Johnson Space Center, Houston, TX, USA",
        "type": "Press Event",
        "description": "NASA will honor the first class of astronaut candidates to graduate under the Artemis program at 10:30 a.m. EST Friday, Jan. 10, at the agency’s Johnson Space Center in Houston. After completing more than two years of basic training, these candidates will become eligible for spaceflight, including assignments to the International Space Station, Artemis missions to the Moon, and ultimately, missions to Mars.",
        "url": "https://lldev.thespacedevs.com/2.2.0/event/77/",
        "news_url": "https://www.nasa.gov/press-release/nasa-s-astronaut-candidates-to-graduate-with-eye-on-artemis-missions",
        "video_url": "https://www.youtube.com/watch?v=xo58EoT987M",
        "feature_image": "https://spacelaunchnow-prod-east.nyc3.digitaloceanspaces.com/media/event_images/20172520nasa2520astronaut2520class2520graduation2520ceremony_image_20191228100802.jpg"
    },
    {
        "id": 60,
        "name": "70th International Astronautical Congress",
        "date": "2019-10-25T21:00:00Z",
        "location": "Washington D.C, United States",
        "type": "Press Event",
        "description": "The International Astronautical Congress is a yearly conference where key figures in the space industry meet and showcase/discuss events in the spaceflight industry.\r\n\r\nThe event lasts starts on 21st October and lasts a week. Some of the panels will be live streamed for free on NASA TV.",
        "url": "https://lldev.thespacedevs.com/2.2.0/event/60/",
        "news_url": "https://www.iac2019.org/",
        "video_url": "https://www.youtube.com/watch?v=21X5lGlDOfg",
        "feature_image": "https://spacelaunchnow-prod-east.nyc3.digitaloceanspaces.com/media/event_images/70th2520international2520astronautical2520congress_image_20191019002059.png"
    },
    {
        "id": 198,
        "name": "8th meeting of the National Space Council",
        "date": "2020-12-09T17:30:00Z",
        "location": "Kennedy Space Center",
        "type": "Press Event",
        "description": "US Vice President Mike Pence will convene the 8th meeting of the National Space Council at NASA's Kennedy Space Center on December 9 at 12:30 p.m. ET. \r\n\r\nThe meeting will be livestreamed on NASA TV.",
        "url": "https://lldev.thespacedevs.com/2.2.0/event/198/",
        "news_url": null,
        "video_url": "https://www.youtube.com/watch?v=21X5lGlDOfg",
        "feature_image": "https://spacelaunchnow-prod-east.nyc3.digitaloceanspaces.com/media/event_images/8th_meeting_of__image_20201201090808.jpeg"
    }
]
```
* http://localhost:{port}/api/upcoming
```javascript
[
    {
        "id": 275,
        "name": "CRS-23 Dragon Docking",
        "date": "2021-08-19T00:00:00Z",
        "location": "International Space Station",
        "type": "Docking",
        "description": "Following its launch atop a Falcon 9, the CRS-23 Dragon will autonomously dock to the ISS, bringing crew supplies as well as experiments.",
        "url": "https://lldev.thespacedevs.com/2.2.0/event/275/",
        "news_url": null,
        "video_url": "https://www.youtube.com/watch?v=21X5lGlDOfg",
        "feature_image": "https://spacelaunchnow-prod-east.nyc3.digitaloceanspaces.com/media/event_images/crs-23_dragon_d_image_20210519074125.jpeg"
    },
    {
        "id": 276,
        "name": "CRS-23 Dragon Undocking",
        "date": "2021-09-12T00:00:00Z",
        "location": "International Space Station",
        "type": "Undocking",
        "description": "The SpaceX CRS-23 Dragon spacecraft will undock from the International Space Station ahead of its reentry, splashdown and recovery.",
        "url": "https://lldev.thespacedevs.com/2.2.0/event/276/",
        "news_url": null,
        "video_url": "https://www.youtube.com/watch?v=21X5lGlDOfg",
        "feature_image": "https://spacelaunchnow-prod-east.nyc3.digitaloceanspaces.com/media/event_images/crs-23_dragon_u_image_20210519074227.jpeg"
    }
]
```
* http://localhost:{port}/api/event?name=Apollo+11th+50th+Anniversary
```javascript
{
    "id": 25,
    "name": "Apollo 11th 50th Anniversary - Lunar Landing",
    "date": "2019-07-20T20:17:00Z",
    "picture_of_the_day": {
        "hdurl": "https://apod.nasa.gov/apod/image/1907/a11pan1040226lftsm.jpg",
        "explanation": "Have you seen a panorama from another world lately? Assembled from high-resolution scans of the original film frames, this one sweeps across the magnificent desolation of the Apollo 11 landing site on the Moon's Sea of Tranquility. The images were taken by Neil Armstrong looking out his window of the Eagle Lunar Module fifty years ago, shortly after the July 20, 1969 landing. The frame at the far left (AS11-37-5449) is the first picture taken by a person on another world. Toward the south, thruster nozzles can be seen in the foreground on the left, while at the right, the shadow of the Eagle is visible to the west. For scale, the large, shallow crater on the right has a diameter of about 12 meters. Frames taken from the Lunar Module windows about an hour and a half after landing, before walking on the lunar surface, were intended to initially document the landing site in case an early departure was necessary."
    },
    "location": "Lunar Surface",
    "type": "Moon Landing",
    "description": "The United States' Apollo 11 was the first crewed mission to land on the Moon, on 20 July 1969. To date, the United States is the only country to have successfully conducted crewed missions to the Moon, with the last departing the lunar surface in December 1972.\r\n\r\nA total of twelve men have landed on the Moon. This was accomplished with two US pilot-astronauts flying a Lunar Module on each of six NASA missions across a 41-month period starting 20 July 1969 UTC, with Neil Armstrong and Buzz Aldrin on Apollo 11, and ending on 14 December 1972 UTC with Gene Cernan and Jack Schmitt on Apollo 17. Cernan was the last to step off the lunar surface.",
    "url": "https://lldev.thespacedevs.com/2.2.0/event/25/",
    "news_url": "https://www.nasa.gov/feature/apollo-11-in-real-time-50-years-later/",
    "video_url": "https://apolloinrealtime.org/11/",
    "feature_image": "https://spacelaunchnow-prod-east.nyc3.digitaloceanspaces.com/media/event_images/apollo252011th2520-2520lunar2520landing252050th2520anniversary_image_20190715211113.jpg"
}
```