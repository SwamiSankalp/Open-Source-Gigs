## Medusa Enhancement Requests

All of the enhancement and feature requests for *[Medusa](https://medusajs.com/)* are listed here, and community can pick the ones they want to complete and be rewarded for completing them.

## Code Enhancement/Feature Requests
---

**1. Support filtering price lists by customer groups**

We want to add support for filtering by customer groups. We should extend the `FitlerablePriceListProps` here to include a `customer_group_id?` field of type `string[]` which would include the list of customer group ids to filter by.

  - **Posted by**: *[@zakariaelas](https://github.com/zakariaelas)*
  - **Status**: *Not Assigned*
  - **Standard**: *Non-paid*
  - **[Issue Link](https://github.com/medusajs/medusa/issues/1286)**

---

**2. API: Complete a batch operation**

Completes a previously dry_run'ed job.

```
POST /admin/batch/:id/complete
```
**DoD**
  - [ ] should be idempotent - i.e. if trying to complete a job that is currently processing the completion step then nothing should happen and endpoint should respond 200
  - [ ] only your own jobs can be completed i.e. `req.user.id === batch.created_by` must be true
  - [ ] should call `BatchJobService.complete` which in turn calls the underlying handler.
  - [ ] Endpoint should not wait for the actual processing of the job to complete

 - **Posted by**: *[@srindom](https://github.com/srindom)*
 - **Status**: *Not Assigned*
 - **Standard**: *Non-paid*
 - **[Issue Link](https://github.com/medusajs/medusa/issues/1277)**

---

**3. API: Cancel a batch operation**

 Cancels an operation that is in progress.

```
POST /admin/batch/:id/cancel
```
**DoD**
 - [ ] endpoint should be idempotent - e.g. calling cancel on an already canceled job is allowed and responds with 200
 - [ ] BatchJobs in a completed state should not be cancelable - should fail with 422
 - [ ] Should call BatchJobService.cancel; which in turn potentially cancels the jobs in the worker that are currently being processed.
 
 - **Posted by**: *[@srindom](https://github.com/srindom)*
 - **Status**: *Not Assigned*
 - **Standard**: *Non-paid*
 - **[Issue Link](https://github.com/medusajs/medusa/issues/1276)**

---

**4. API: List batch operations**

 Lists the BatchJobs created by the authenticated user.

```
GET /admin/batch

Response
- count
- limit
- offset
- batch_jobs - { id, status, progress, ... }
```
**DoD**
 - [ ] should respond with the batch jobs that are created by the user
 - [ ] calls `BatchJobService.listAndCount`
 
 - **Posted by**: *[@srindom](https://github.com/srindom)*
 - **Status**: *Not Assigned*
 - **Standard**: *Non-paid*
 - **[Issue Link](https://github.com/medusajs/medusa/issues/1275)**

---
