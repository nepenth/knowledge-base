## Definition
A deadlock is a situation where two or more processes are unable to proceed because each is waiting for the other to release resources. It's essentially a circular wait condition that results in all involved processes being blocked indefinitely.

## Key Characteristics of Deadlocks
- **Mutual Exclusion**: Resources cannot be shared simultaneously.
- **Hold and Wait**: Processes hold resources while waiting for additional ones.
- **No Preemption**: Resources cannot be forcibly taken away from processes.
- **Circular Wait**: A circular chain of processes, each waiting for resources held by the next.

## Common Examples
1. **Dining Philosophers Problem**:
   - Multiple philosophers sharing a limited number of chopsticks
   - Each philosopher needs two chopsticks to eat
   - Deadlock occurs when all philosophers pick up one chopstick and wait for another

2. **Database Transactions**:
   - Two transactions trying to update the same records
   - Transaction A locks record 1, waits for record 2
   - Transaction B locks record 2, waits for record 1

## Prevention Strategies
### 1. Avoiding Circular Wait
- Implement resource ordering
- Require processes to request all resources at once
- Use timeouts when requesting resources

### 2. Breaking Mutual Exclusion
- Allow resource sharing where possible
- Use spooling or buffering techniques

### 3. Preventing Hold and Wait
- Implement pre-allocation of resources
- Use resource hierarchy systems

## Detection Methods
1. **Resource Allocation Graph**:
   - Represents processes, resources, and their relationships
   - Identifies potential deadlock situations

2. **Banker's Algorithm**:
   - Safely allocates resources to prevent deadlocks
   - Simulates resource requests before granting them

## Recovery Techniques
- **Process Termination**: Forcefully terminating one or more processes
- **Resource Preemption**: Taking resources away from processes
- **Rollback**: Returning processes to a previous safe state

## Key Takeaways
1. Deadlocks are serious system issues that require careful handling
2. Prevention is better than recovery in most cases
3. Resource management and proper process design can minimize deadlock risks
4. Regular monitoring and detection systems should be implemented

## References
- Operating Systems: Three Easy Pieces (happily studying operating systems)
- The Art of Multiprocessor Programming by Maurice Herlihy and Nir Shavit
- Deadlock Prevention, Avoidance and Detection in Modern Operating Systems

---
**Source**: [Original Tweet](https://twitter.com/i/web/status/1911084003957833860)