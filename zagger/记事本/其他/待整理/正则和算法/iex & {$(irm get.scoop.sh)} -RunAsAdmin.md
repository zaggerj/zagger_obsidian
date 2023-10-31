# iex & {$(irm get.scoop.sh)} -RunAsAdmin

　　iex "& {\$(irm get.scoop.sh)} -RunAsAdmin"

　　iwr -useb get.scoop.sh \| iex

　　\$env:SCOOP='D:\Applications\Scoop'

　　\[Environment\]::SetEnvironmentVariable('SCOOP', \$env:SCOOP, 'User')

　　\$env:SCOOP_GLOBAL='D:\GlobalScoopApps'

　　\[Environment\]::SetEnvironmentVariable('SCOOP_GLOBAL', \$env:SCOOP_GLOBAL, 'Machine')
