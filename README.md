# FreeBSD_x3399

## install 
This board uart is 1.25mm , need 1.24mm to 2.54 cable
uart:

vcc
txd
rxd
gnd
cpu fan

(Rock960)[https://wiki.freebsd.org/arm64/Rock960]
(ROCKPro64)[https://wiki.freebsd.org/arm64/ROCKPro64]

Ethernet card can't found , currently I use a usb WI-FI card .
## issue 

This board have gmac,but u-boot.idb version dones'nt include it.
need rebuild  u-boot.idb  file ,use rockchip-x3399.dtb
```
	ethernet@fe300000 {

		compatible = "rockchip,rk3399-gmac";
		reg = <0x0 0xfe300000 0x0 0x10000>;
		rockchip,grf = <0x17>;
		interrupts = <0x0 0xc 0x4 0x0>;
		interrupt-names = "macirq";
		clocks = <0x8 0x69 0x8 0x67 0x8 0x68 0x8 0x66 0x8 0x6a 0x8 0xd5 0x8 0x166>;
		clock-names = "stmmaceth", "mac_clk_rx", "mac_clk_tx", "clk_mac_ref", "clk_mac_refout", "aclk_mac", "pclk_mac";
		resets = <0x8 0x89>;
		reset-names = "stmmaceth";
		power-domains = <0x18 0x16>;
		status = "okay";
		phy-supply = <0x19>;
		phy-mode = "rgmii";
		clock_in_out = "input";
		snps,reset-gpio = <0x1a 0xf 0x1>;
		snps,reset-active-low;
		snps,reset-delays-us = <0x0 0x2710 0xc350>;
		assigned-clocks = <0x8 0xa6>;
		assigned-clock-parents = <0x1b>;
		pinctrl-names = "default";
		pinctrl-0 = <0x1c>;
		tx_delay = <0x28>;
		rx_delay = <0x11>;
	};
```