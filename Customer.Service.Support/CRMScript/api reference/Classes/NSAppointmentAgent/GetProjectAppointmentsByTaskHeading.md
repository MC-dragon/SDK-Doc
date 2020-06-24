---
title: NSAppointment[] GetProjectAppointmentsByTaskHeading(Integer projectId, DateTime startTime, DateTime endTime, Integer count, Integer taskHeadingId)
path: /EJScript/Classes/NSAppointmentAgent/Member functions/NSAppointment[] GetProjectAppointmentsByTaskHeading(Integer p_0, DateTime p_1, DateTime p_2, Integer p_3, Integer p_4)
intellisense: 1
classref: 1
sortOrder: 861
keywords: GetProjectAppointmentsByTaskHeading(Integer,DateTime,DateTime,Integer,Integer)
---


Method that returns a specified number of appointments of a specific appointment task heading within a time range. The appointments belong to the project specified.  Task represents the different types of activities, like “Phone call”, “Meeting” and so on. The heading represents a grouping or filtering of tasks.



* **projectId:** The project id
* **startTime:** The start of the time interval we want appointments from. This will usually be the current time.
* **endTime:** The end of the time interval.
* **count:** The maximum number of appointments that should be returned. -1 means no count restrictions.
* **taskHeadingId:** The task heading id. The heading represents a grouping or filtering of tasks. Task represents the different types of activities, like “Phone call”, “Meeting” and so on.
* **Returns:** Array of Appointments.

