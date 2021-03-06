# mx_job_create

## NAME

job_create - create a new job

## SYNOPSIS

```
#include <magenta/syscalls.h>

mx_status_t mx_job_create(mx_handle_t job, uint32_t options, mx_handle_t* out);

```

## DESCRIPTION

**job_create**() creates a new child [job object](../objects/job.md) given a
parent job.

Upon success a handle for the new job is returned.

Job handles may be waited on (TODO(cpu): expand this)

## RETURN VALUE

**job_create**() returns NO_ERROR and a handle to the new job
(via *out*) on success.  In the event of failure, a negative error value
is returned.

## ERRORS

**ERR_BAD_HANDLE**  *job* is not a valid handle.

**ERR_WRONG_TYPE**  *job* is not a job handle.

**ERR_INVALID_ARGS**  *options* is nonzero,
or *out* is an invalid pointer.

**ERR_ACCESS_DENIED**  *job* does not have the **MX_RIGHT_WRITE** right.

**ERR_NO_MEMORY**  (Temporary) Failure due to lack of memory.

**ERR_BAD_STATE**  (Temporary) Failure due to the job object being in the
middle of a *mx_task_kill()* operation.

## SEE ALSO

[process_create](process_create.md),
[task_kill](task_kill.md).
