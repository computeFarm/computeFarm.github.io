# ComputeFarm

A ComputeFarm is a collection of tools to manage a complex computation
across a number of remote workers.

The primary requirements, are that a ComputeFarm should:

1. require minimal intervention of a systems administrator, and

2. be light weight enough that end users can "share" remote workers across
   "spare" or "under used" computers.

A ComputeFarm is *not* intended to be a replacement for a Kubernetes based build
system. (However a ComputeFarm could (potentially) be run across a Kubernetes
based build system, *BUT* this *would* require a systems administrator to setup).

The *one* thing you might require a systems administrator's help is in allowing
traffic through your firewall on *one* port. (See [setup]() for details)

----

A ComputeFarm consists of the following tools:

1. A "MajorDomo" command line tool run by an end user to orchestrate the various
   steps in a computation. The MajorDomo is based upon the
   [`doit`](https://github.com/pydoit/doit) tool and acts more or less like a
   very intelligent "CMake" / "make".

2. A "TaskManager" process run by the compute farm on the end user's main
   computer. The task manager receives task requests from the MajorDomo
   and assigns them to one or more (remote) workers. The task manager also
   receives load information from the monitors on each machine in the
   compute farm.

3. A "LogManager" ([`cuteLogs`](https://github.com/busimus/cutelog)) to allow
   the end user to monitor the on going progress of the computation. This is a
   Python GUI which runs on the end user's main computer.

4. A "Monitor" process on all machines in the compute farm. This monitor
   periodically informs the task manager of the load on a given machine.

5. A number of specialised "Worker" processes spread across the machines
   in a compute farm. Each specialised worker understands how to complete
   one type of task.

----

To function, a ComputeFarm requires a full description of the problems it
needs to solve as well as the capabilities it has to solve these problems.

Each "Worker" needs descriptions of

1. what it can do (capabilities)

The "MajorDomo" needs descriptions of

1. what problem needs to be solved, expressed largely by the capabilities and
   actions required to solve this problem.

2. how to contact the ComputeFarm

3. what capabilities each worker is able to provide

