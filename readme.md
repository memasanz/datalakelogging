Azure Data Lake Gen2 Logging Capabilities
=========================================

Setting Diagnostic Settings to log into Log Analytics Workspace:

![Graphical user interface, text, application, email Description automatically generated](media/c63b2840c8629bff2aaeec2fdfd13679.png)

![Table Description automatically generated](media/7fdf7279e6d9dfb33fde9df00a2347ea.png)

StorageBlobLogs

\| where AuthenticationType == 'OAuth'

\| summarize count() by RequesterAppId

\| render piechart

StorageBlobLogs

\| where TimeGenerated \> ago(3d)

\| summarize count() by OperationName

\| sort by count\_ desc

\| render piechart

![Chart, pie chart Description automatically generated](media/e3dc380a6efd2bf9918da353438fefcf.png)

StorageBlobLogs

\| where TimeGenerated \> ago(3d)

\| top 10 by DurationMs desc

\| project TimeGenerated, OperationName, DurationMs, ServerLatencyMs,
ClientLatencyMs = DurationMs – ServerLatencyMs

StorageBlobLogs

\| where TimeGenerated \> ago(3d) and StatusText !contains "Success"

\| summarize count() by OperationName

\| top 10 by count\_ desc
