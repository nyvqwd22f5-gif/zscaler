# Deleting Events
Source: https://help.zscaler.com/itdr/deleting-events
PDF: https://help.zscaler.com/pdf/com/en/1531826.pdf

On the [Event Logs](/itdr/about-event-logs) page, you can see all the events associated with a particular entity, such as attackers or endpoints. You can delete events from the Event Logs page to remove them permanently.
To delete events:
-
On the [extended details](/itdr/viewing-extended-details) page of an entity from the dashboard, click **Event Logs**.
The **Event Logs** page appears.
- On the **Event Logs** page:
- [Delete specific events](#delete-specific-events)
- [Delete all events](#delete-all-events)
-
[]Select the events that you want to delete.
The option to delete specific events works well when the number of events is less than 100. If you want to delete all events, use the **Delete All** option, especially if the number of events is greater than 100.
-
Select **Delete **from the **Actions **drop-down menu.
[See image.](#delete-option)
-
Confirm your action.
The selected events are removed permanently from the entity.
-
[]Select **Delete All** from the **Actions **drop-down menu.
[See image.](#delete-all-events-image)
-
Confirm your action.
All events are removed from the entity permanently.
- The removal of all events from an entity takes more time than deleting specific events. It can take a few minutes for the UI to reflect the complete removal of events.
- The **Delete All** option removes a maximum of 100K events at a time. If you have more than 100K events associated with an entity, make sure you repeat these steps.
[]
![Option to Delete Events](/downloads/itdr/investigate/extended-details/event-logs/deleting-events/itdr-delete-selected-event-logs.png)
[]
![Event Logs Page](/downloads/itdr/investigate/extended-details/event-logs/deleting-events/itdr-delete-all-events.png)