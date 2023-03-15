过滤rdp事件

Get-WinEvent -FilterHashtable @{logname='Microsoft-Windows-TerminalServices-RemoteConnectionManager/Operational'} -MaxEvents 20 | ft -wrap TimeCreated,Message