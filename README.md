# no-defender
no-defender re-up
# no-defender

A slightly more fun way to disable windows defender.

![](https://i.imgur.com/8qyJoBV.png)

## How it works

There's a WSC (Windows Security Center) service in Windows which is used by antiviruses to let Windows know that there's some other antivirus in the hood and it should disable Windows Defender.  
This WSC API is undocumented and furthermore requires people to sign an NDA with Microsoft to get its documentation, so I decided to take an interesting approach for such a thing and used an already existing antivirus called Avast. This AV engine includes a so-called `wsc_proxy.exe` service, which essentially sets up the WSC API for Avast.  
With a little bit of reverse engineering, I turned this service into a service that could add my own stuff there.

## Limitations

Sadly, to keep this WSC stuff even after reboot, no-defender adds itself (not really itself but rather Avast's module) to the autorun. Thus, you would need to keep the no-defender binaries on your disk :(

## Usage
```commandline
Usage: no-defender-loader [--help] [--version] [--disable] [--firewall] [--av] [--name VAR]

Optional arguments:
  -h, --help     shows help message and exits
  -v, --version  prints version information and exits
  --disable      re-enable firewall/defender
  --firewall     disable the firewall
  --av           disable the defender
  --name         av name [default: "github.com/es3n1n/no-defender"]
```

## License
GPL-3.0
