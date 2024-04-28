# NixOSChuwiMinibookXN100
NixOS configuration on Chuwi Minibook X N100

## Not Working
* Night light does not work
* BIOS does not support rotating display

### Not Working Workarounds
* WiFI and Bluetooth with newer linux kernel in /etc/nixos/configuration.nix:
```
boot.kernelPackages = pkgs.linuxPackages_latest;
```
* Kernel boot logs display can be rotated with kernel parameters in /etc/nixos/configuration.nix:
```
boot.kernelParam = [
  "fbcon=rotate:1"
];
```
* Rotate login screen with arandr param configuration in /etc/nixos/configuration.nix:
```
services.xserver.xrandrHeads = [
{
  monitorConfig = "Option \"Rotate\" \"right\"";
  output = "DSI-1";
}
];
```
