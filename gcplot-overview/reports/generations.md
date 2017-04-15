# Generations

This is where the most detailed stats & info about each GC Generation falls. There are tables with total, occupied sizes by Generation, as well as STW pauses graphs, and, finally, the numerous statistical info, like Total, Min/Max, Average pause times, average interval between events and so on.

One note should be done here. Consider next table:

| Generation | Average | Min | Max |
| :--- | :--- | :--- | :--- |
| Young | `1.995 GB` | `25.255 MB` | `2.197 GB` |
| Tenured | `4.691 GB` | `2.132 GB` | `7.612 GB` |
| Heap | `6.672 GB` | `2.420 GB` | `9.643 GB` |

Each cell contains **average/min/max observed** value for the given generation. So, the rule like Young+Tenured=Heap may not work here.

For example: at one point of time we observed min Young as `5mb`, and in another time Tenured min was `10mb`. At third time we noticed Heap min size as `15mb`. At first glance, all three events were at the same time! But if `-XX:+UseAdaptiveSizePolicy` was enabled, all the magic ruins. When Young was just `5mb`, the Tenured easily might be `1gb`. So, please be accurate in your analysis and estimation.

