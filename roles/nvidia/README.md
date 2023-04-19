# README
Helpful links
- Nvidia Kubernetes installation guide: <https://docs.nvidia.com/datacenter/cloud-native/kubernetes/install-k8s.html#install-k8s>.
- Linux driver downloads: <https://download.nvidia.com/XFree86/Linux-x86_64>.

## Node setup
- A set of notes during my Nvidia VM setup.
```
ESXi Host BIOS setup:
Enable SR-IOV
Enable Above 4G decoding
Enable iGPU and make it the primary graphics card

VM memory settings:
Reserve all guest memory (All locked)

VM advanced aarameters:
pciPassthru.use64bitMMIO	TRUE
pciPassthru.64bitMMIOSizeGB	64
pciPassthru.msiEnabled	FALSE
hypervisor.cpuid.v0	FALSE

# cat /etc/modprobe.d/nvidia.conf
options nvidia NVreg_OpenRmEnableUnsupportedGpus=1

# update-initramfs -u

Installing drivers:
apt-get install build-essential linux-headers-$(uname -r)

# cat /etc/modprobe.d/nvidia.conf
options nvidia NVreg_OpenRmEnableUnsupportedGpus=1
# update-initramfs -u

Found here: https://download.nvidia.com/XFree86/Linux-x86_64
./NVIDIA-Linux-x86_64-530.41.03.run -m=kernel-open  --disable-nouveau --silent
```
