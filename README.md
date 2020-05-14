## nsxez

NSXEZ is a Python library to remotely manage/automate NSX-T platforms. The user is NOT required to be a Software Programmer, or have sophisticated knowledge of NSX-T environments, or have a complex understanding of the NSX-T REST API. It does however expect that someone has built a functional NSX-T environment which includes a functional Tier-0 router and potentially edge gatway services...if you expect to have any decent functionality. 


## Installation

Installation requires Python 2.7 or 3.X and the associated python pip tool. The only other requirements currently as the requests and uuid libraries which are installed automatically through pip. To install nsxez simply use the following command from your shell, provided pip is installed and operational. 

`
pip install nsxez
`

## Upgrade

Upgrading has the same requiremetns as installation and has the same format for install with the addition of -U 

`
pip install -U nsxez
`

