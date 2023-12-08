# scalable-apscheduler
`docker-compose up --build`

### learnings
- apscheduler is not suitable for distributed systems as it is not scalable.
- When running more than 1 instance of scheduler with redis as the persistent job store, both schedulers are able to modify the trigger datetime of the same job based on the job id.
- However, upon trigger, all instances will run the callback, instead of just once (expected behaviour). 
- This is because locks are implemented only at the process level, not at the persistent store level.