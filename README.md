# NixOSChuwiMinibookXN100
NixOS configuration on Chuwi Minibook X N100

## Not Working
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
* Use redshift for night light configured in /etc/nixos/configuration.nix
```
  location.latitude = 100.0;
  location.longitude = -100.0;
  location.provider = "manual";
  services.redshift = {
    enable = true;
    brightness = {
      # Note the string values below.
      day = "1";
      night = "1";
    };
    temperature = {
      day = 6500;
      night = 3700;
    };
  };
```
