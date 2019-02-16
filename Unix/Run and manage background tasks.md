# Run and manage background tasks

Add a trailing ampersand `&` to background a task. The job id is returned (eg. `[1]` represents Job 1)

    <command> &

View current running jobs

    jobs

Terminate a job

    kill %<id>
    kill %1

Bring a background process to the foreground

    fg
    fg %<id>
    fg %1
