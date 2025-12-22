## EXPRESSCLUSTER Battle Card vs. Veeam or vSphere Replicaiton

## Elevator pich

Achieve Zero RPO (no data loss) with EXPRESSCLUSTER while Veeam and vSphere Replication cannot prevent data-loss.

Both Veeam and vSphere Replication replicate VM images through asynchronous copying (which can be regarded as a form of backup) and start the replicated VM in the event of a failure. Consequently, any data changes made between the creation of the replica and the occurrence of the failure are lost. There is always an RPO (Recovery Point Objective), a relatively long RTO (Recovery Time Objective) is required, and no-data-loss cannot be achieved.
In contrast, the typical use of ECX replication is to duplicate application data through synchronous copying. As a result, the point of failure itself becomes the RPO, enabling no-data-loss. Furthermore, the RTO is relatively short—usually within five minutes.

| Item                           | Veeam / vSphere Replication                           | ECX Replication
|--                              |--                                                     |--
| Copy Method                    | Asynchronous copy (backup-like replication)           | Synchronous copy (application data replication)
| Data Loss                      | Changes between replica creation and failure are lost | Point of failure becomes RPO, enabling no-data-loss
| RPO (Recovery Point Objective) | Always present                                        | At failure time = RPO (effectively zero)
| RTO (Recovery Time Objective)  | Relatively long                                       | Relatively short (usually within 5 minutes)
| Characteristics                | Backup-oriented, but cannot achieve no-data-loss      | Combines fast recovery with no-data-loss

## Qualifying questions

Do you have data that must not be lost, no matter what the situation?

⇒ You lose data from the time of the last backup to the time of the failure if you protect a VM using Veeam or vSphere Replication. 
