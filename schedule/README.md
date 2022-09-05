# Django - Schedule

This is an api for scheduling meeting rooms.  
## Scenario  

This system must receive scheduling requests containing title, room and scheduling period, and
should only reserve the room if the requested room is available. Otherwise it should display an error. 
  

## Deliverables  

- [x] An API for creating, editing and removing meeting rooms
- [x] An API for creating, editing and removing schedules
- [x] Prevent concurrent appointments(Model)
- [x] Prevent concurrent appointments(URL)
- [x] An API to list and filter bookings by date and room
- [x] Running on Docker with Postgres and gunicorn
  

## How to run (docker-compose) 
- Path to the folder where the `Dockerfile` file is
    ```bash
        docker-compose up --build
    ``` 
- There may be some permission problems in the postgre directory so use the following command:
    ```sudo chown $USER:$USER postgres_data/ -R```

## How to run (without docker-compose) 
- Path to the folder where the `manage.py` file is
- Set up the database of your choice in ```agenda_me/agenda_me/settings.py```

    ``bash    
        pip install -r requirements.txt
        python manage.py runserver

    ``` 

## Urls

### Rooms
---
- List all rooms:

	- [GET] http://localhost:8000/sala/
---
- Get a room's data:

	- [GET] http://localhost:8000/sala/1
---
- Create a room:

	- Fields: 
	```
		{
		  "name" : "Room 01 Xpto"
		}
	```
	- [POST] http://localhost:8000/sala/
---
- Edit a room:	
	- Fields: 
	```
		{
		  "name" : "Room 01 Xpto"
		}
	```
	- [PUT] http://localhost:8000/sala/1
---
- Remove a room:
	- [DELETE] http://localhost:8000/sala/1

  

### Schedules
---
- List all schedules:

	- [GET] http://localhost:8000/agenda/
---
- Get data from a schedule:

	- [GET] http://localhost:8000/agenda/1
---
- Create a schedule:
	- Fields:
	```
		{
		  "title": "ABC Meeting",
		  "room" : "1",
		  "date_init" : "2019-01-01 14:30",
		  "date_end" : "2019-01-01 16:30"
		}
	```
	- [POST] http://localhost:8000/agenda/
---
- Edit a schedule:
	
	- Fields:
	```
		{
		  "title": "ABCDeE meeting",
		  "room" : "1",
		  "date_init" : "2019-01-01 14:30",
		  "date_end" : "2019-01-01-01 16:30"
		}
	```

	- [PUT] http://localhost:8000/agenda/1
---
- Remove a schedule:

	- [DELETE] http://localhost:8000/agenda/1
---
- Fetch schedule for a specific room

	- [GET] http://localhost:8000/agenda/?sala=1
---
- Search for schedule between specific dates

	- [GET] http://localhost:8000/agenda/?data_inicial=2019-01-01&data_final=2019-12-12
---
- Search agenda between specific dates and specific room

	- [GET] http://localhost:8000/agenda/?data_inicial=2019-01-01&data_final=2019-12-12&sala=1
---
  
## Run the Tests

```bash
  python -W ignore manage.py test 
```
## Test Coverage 

```bash

coverage erase; coverage run --source=salas,agenda manage.py test; coverage report
```

|Name | Stmts |Miss| Cover|
|-|-|-|-|
|agenda/models.py |24 |0 |100%
|agenda/serializers.py |19 |0 |100%
|agenda/views.py |25 |0 |100%
rooms/models.py |8 |0 |0 |100%
|salas/serializers.py |8 |0 |0 |100%
|Homes/views.py.py |11 |0 |100%
## Total |95 |0 |100% ## Other tests   


## Other tests

- I also left the `postman` file to test if you want: 

`Maga.postman_collection.json`