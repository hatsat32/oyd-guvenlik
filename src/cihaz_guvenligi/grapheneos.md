# GrapheneOS Kurulumu

GrapheneOS güvenlik odaklı bir Android projesi. Proje Google Pixel cihazların donanımsal özellikleri ile birlikte güvenlik özelliklerinin varsayılan olarak geldiği bir dağıtım sağlamakta.

GrapheneOS'in kurulumu proje tarafından hazırlanan rehber ve betik sayesinde fazlasıyla kolay. Bu rehber [Grapheneos'in web sitesindeki](https://grapheneos.org/install) kurulum rehberinden çeviridir. Keza proje kısıtlı sayıda cihazda çalıştığından kurulum fazlasıyla belgelenmiş ve iyileştirilmiş durumda. Kimi değişiklikler ise kolaylık ve anlaşılırlık amacı ile eklenmiştir rehbere.

## Kurulum

Bu rehber GrapheneOS'in resmen desteklenen cihazlarına ilişkindir. Hem projenin hem de özel kurulumlar için kullanılabilir.

## Gereksinimler

En az 2GB boş hafızaya sahip olmalısınız.

Windows 10, macOS Catalina, Arch Linux, Debian buster ve Ubuntu 20.04 LTS GraphenOS'in kurulumu için desteklenen işletim sistemleridir. Bu işletim sistemlerinden birinin güncel haline kuruluma devam etmeden önce sahip olmalısınız. Eski sürümler ve diğer GNU/Linux dağıtımları genellikle çalışmakla birlikte bir sorunla karşılaşmanız durumunda desteklenen işletim sistemlerinden birini denemeniz önerilir. 

Desteklenen cihazlardan birine sahip olmanız gerekli. Cihazınızın kilidinin açılıp GrapheneOS kurulabilmesini garanti etmek için operatörlerin sattığı cihazlardan uzak durmanız önerilir. Operatörler tarafından satılan cihazlar aynı işletim sistemi ve firmware'i içermekle birlikte cihazda operatöre özel ayarların açılabilmesi için bir ID ile birlikte gelmekte. Bu ayarlar bootloader'in kilidinin açılmasını engellemekte. Operatörler bunu devreden çıkarabilecek olsalar da destek ekibinin bunu bilmeme ihtimali yüksek ve olsa bile bunu yapmayabilirler. Operatörlerden bağımsız bir cihaz edinerek bu tehlikeden ve potansiyel dertlerden uzak kalabilirsiniz. Eğer operatör cihazının kilidini açabilirseniz bu GrapheneOS için bir sorun teşkil etmeyecektir.

Cihazın standart işletim sistemini güncellemek ve buradaki önergeleri takip etmeden önce en güncel firmware'i çalıştırdığından emin olmakta fayda var. Bu şekilde olası sorunlara, eksik özelliklere ve eski sürümlerdeki diğer değişikliklerle karşılaşmanın önüne geçilebilir. Dilerseniz cihazınızı online olarak güncelleyebilir veya Pixel cihazlara has tam güncelleme paketini yükleyebilirsiniz.

These instructions use command-line tools. On Windows, use PowerShell rather than the legacy Command Prompt.

Bu rehber komut satırı araçları kullanmakta. Windows'ta eski komut satırı yerine PowerShell kullanılmakta.

### Fastboot kurulumu

Fastboot'un güncel bir kopyasını edinmeniz ve işletim sisteminizde PATH çevresel değişkenine ekli olmalıdır. `fastboot --version` komutunu çalıştırarak hangi sürüme sahip olduğunuzu görebilirsiniz. Sürümünüz en az ** 29.0.6. ** olmalıdır. Dağıtımınızın paket yöneticisini kurulum için kullanabilirsiniz lakin pek çok paket deposu fastboot'un geliştirici sürümünü bulundurmakta, standart versiyon platform-tools (adb, fastboot, etc) kendilerine göre düzenleyip güncel tutmamakta.

Dağıtım paketlerinin listesi:


* __Arch Linux:__ `android-tools` fastboot ve diğer gerekli araçları getirmekte ve 

android-tools provides fastboot and other useful tools not required for installation such as adb. android-udev provides udev rules allowing fastboot and adb to work in local sessions without root.
* __Debian:__ package is both broken and out-of-date, do not use (see paragraph above)
* __Ubuntu:__ package is both broken and out-of-date, do not use (see paragraph above)

Standalone platform-tools

If your operating system doesn't make a proper version of fastboot available, consider using the standalone releases of platform-tools from Google. If you have the Android SDK or intend to do development work, you install the platform-tools package via the Android SDK package manager which can be used to keep it up-to-date. The Android SDK is available by itself or can be obtained via Android Studio.

To download, verify and extract the standalone platform-tools on Linux:

curl -O https://dl.google.com/android/repository/platform-tools_r30.0.4-linux.zip
echo '5be24ed897c7e061ba800bfa7b9ebb4b0f8958cc062f4b2202701e02f2725891  platform-tools_r30.0.4-linux.zip' | sha256sum -c
unzip platform-tools_r30.0.4-linux.zip

To download, verify and extract the standalone platform-tools on macOS:

curl -O https://dl.google.com/android/repository/fbad467867e935dce68a0296b00e6d1e76f15b15.platform-tools_r30.0.4-darwin.zip
echo 'SHA256 (fbad467867e935dce68a0296b00e6d1e76f15b15.platform-tools_r30.0.4-darwin.zip) = e0db2bdc784c41847f854d6608e91597ebc3cef66686f647125f5a046068a890' | shasum -c
tar xvf fbad467867e935dce68a0296b00e6d1e76f15b15.platform-tools_r30.0.4-darwin.zip

To download, verify and extract the standalone platform-tools on Windows:

curl.exe -O https://dl.google.com/android/repository/platform-tools_r30.0.4-windows.zip
(Get-FileHash platform-tools_r30.0.4-windows.zip).hash -eq "413182fff6c5957911e231b9e97e6be4fc6a539035e3dfb580b5c54bd5950fee"
tar xvf platform-tools_r30.0.4-windows.zip

Next, add the tools to your PATH in the current shell so they can be used without referencing them by file path, enabling usage by the flashing script.

On Linux and macOS:

export PATH="$PWD/platform-tools:$PATH"

On Windows:

$env:Path = "$pwd\platform-tools;$env:Path"

Sample output from fastboot --version afterwards:

fastboot version 30.0.4-6686687
Installed as /home/username/downloads/platform-tools/fastboot

This is a temporary change to PATH for the current shell and will need to be done again if you open a new terminal. Make sure that the fastboot command works in the current shell before trying to run the flashing script.
Obtaining signify

To verify the download of the OS beyond the security offered by HTTPS, you can use the signify tool. If you do not have a way to obtain signify from a package repository you're already trusting, it does not make sense to use it. GrapheneOS releases are hosted on our servers and we do not have third party mirrors. A compromised signify would be able to compromise your OS and the GrapheneOS download due to the lack of an application security model on traditional operating systems. It would be worse than not trying to verify the signatures. It's far less likely that our servers would be compromised than someone's GitHub account or GitHub itself. You're already trusting these installation instructions from our site, which is hosted on the same static web server infrastructure as the releases.

List of distribution packages:

    Arch Linux: signify
    Debian: signify-openbsd with the command renamed to signify-openbsd
    Ubuntu: signify-openbsd with the command renamed to signify-openbsd

On Debian-based distributions, the signify package and command are an unmaintained mail-related tool for generating mail signatures (not cryptographic signatures) with the final releases from 2003-2004 made directly by the developer via the Debian package without upstream releases. Please pressure them to correct this usability issue.
Enabling OEM unlocking

OEM unlocking needs to be enabled from within the operating system.

Enable the developer options menu by going to Settings ➔ About phone and pressing on the build number menu entry until developer mode is enabled.

Next, go to Settings ➔ System ➔ Advanced ➔ Developer options and toggle on the 'Enable OEM unlocking' setting. This requires internet access on devices with Google Play services as part of Factory Reset Protection (FRP) for anti-theft protection.
Unlocking the bootloader

First, boot into the bootloader interface. You can do this by turning off the device and then turning it on by holding both the Volume Down and Power buttons.

Unlock the bootloader to allow flashing the OS and firmware:

fastboot flashing unlock

The command needs to be confirmed on the device and will wipe all data.
Obtaining factory images

You need to obtain the GrapheneOS factory images for your device to proceed with the installation process.

You can either download the files with your browser or using a command like curl. It's generally easier to use the command-line since you're already using it for the rest of the installation process, so these instructions use curl.

On Windows, remove PowerShell's legacy curl alias for the current shell to avoid needing to reference it as curl.exe instead of curl:

Remove-Item Alias:Curl

Download the factory images public key (factory.pub) in order to verify the factory images:

curl -O https://releases.grapheneos.org/factory.pub

This is the content of factory.pub:

untrusted comment: GrapheneOS factory images public key
RWQZW9NItOuQYJ86EooQBxScfclrWiieJtAO9GpnfEjKbCO/3FriLGX3

The public key has also been published via the official @GrapheneOS Twitter account, the /u/GrapheneOS Reddit account and is available on GitHub. When the current signing key is replaced, the new key will be signed with it.

Download the factory images for the device from the releases page. For example, to download the 2020.05.05.02 release for the Pixel 3 XL (crosshatch):

curl -O https://releases.grapheneos.org/crosshatch-factory-2020.05.05.02.zip
curl -O https://releases.grapheneos.org/crosshatch-factory-2020.05.05.02.zip.sig

Verify the factory images using the signature if you were able to obtain signify from trusted package repositories (see above):

signify -Cqp factory.pub -x crosshatch-factory-2020.05.05.02.zip.sig && echo verified

This will output verified if verification is successful. If something goes wrong, it will output an error message rather than verified.
Flashing factory images

The initial install will be performed by flashing the factory images. This will replace the existing OS installation and wipe all the existing data.

Reboot into the bootloader interface to begin the flashing procedure.

Next, extract the factory images.

On Linux:

unzip crosshatch-factory-2020.05.05.02.zip

On macOS and Windows:

tar xvf crosshatch-factory-2020.05.05.02.zip

Move into the directory:

cd crosshatch-factory-2020.05.05.02

Flash the images with the flash-all script in the directory.

On Linux and macOS:

./flash-all.sh

On Windows:

./flash-all.bat

Wait for the flashing process to complete and proceed to locking the bootloader before using the device as locking wipes the data again.
Troubleshooting

A common issue on Linux distributions is that they mount the default temporary file directory /tmp as tmpfs which results in it being backed by memory and swap rather than persistent storage. By default, the size is 50% of the available virtual memory. This is often not enough for the flashing process, especially since /tmp is shared between applications and users. To use a different temporary directory if your /tmp doesn't have enough space available:

mkdir tmp
TMPDIR="$PWD/tmp" ./flash-all.sh

A majority of failed flashes tend to be caused by substandard USB connectors, plugging in via hubs or bad cables which aren't properly up to the USB standard. The scrollback from a failed flash will contain valuable diagnostic information which is essential in knowing where and how the process went wrong.

Front I/O ports on desktop computer cases and USB 3.1 or USB C on many laptops often aren't implemented properly or are broken in subtle ways, which may cause flashing to fail even on a USB port that works for other peripherals. Older Linux kernels that predate version 5 may have inadequate or patchwork support for USB C or USB 3. If you are installing from a Linux distribution, ensure your distribution uses a modern kernel.

Always use a high quality USB A to USB C cable with a rear USB port directly on your motherboard, and never use a USB hub for flashing. Never install from a virtual machine; USB passthrough in software emulation may be broken or inadequate and this can cause the flashing to fail.
Locking the bootloader

Locking the bootloader is important as it enables full verified boot. It also prevents using fastboot to flash, format or erase partitions. Verified boot will detect modifications to any of the OS partitions (vbmeta, boot/dtbo, product, system, vendor) and it will prevent reading any modified / corrupted data. If changes are detected, error correction data is used to attempt to obtain the original data at which point it's verified again which makes verified boot robust to non-malicious corruption.

In the bootloader interface, set it to locked:

fastboot flashing lock

The command needs to be confirmed on the device since it needs to perform a factory reset.

Unlocking the bootloader again will perform a factory reset.
Disabling OEM unlocking

OEM unlocking can be disabled again in the developer settings menu within the operating system after booting it up again.
Verifying installation

Verified boot authenticates and validates the firmware images and OS from the hardware root of trust. Since GrapheneOS supports full verified boot, the OS images are entirely verified. However, it's possible that the computer you used to flash the OS was compromised, leading to flashing a malicious verified boot public key and images. To detect this kind of attack, you can use the Auditor app included in GrapheneOS in the Auditee mode and verify it with another Android device in the Auditor mode. The Auditor app works best once it's already paired with a device and has pinned a persistent hardware-backed key and the attestation certificate chain. However, it can still provide a bit of security for the initial verification via the attestation root. Ideally, you should also do this before connecting the device to the network, so an attacker can't proxy to another device (which stops being possible after the initial verification). Further protection against proxying the initial pairing will be provided in the future via optional support for ID attestation to include the serial number in the hardware verified information to allow checking against the one on the box / displayed in the bootloader. See the Auditor tutorial for a guide.

After the initial verification, which results in pairing, performing verification against between the same Auditor and Auditee (as long as the app data hasn't been cleared) will provide strong validation of the identity and integrity of the device. That makes it best to get the pairing done right after installation. You can also consider setting up the optional remote attestation service.
Replacing GrapheneOS with the stock OS

Installation of the stock OS via the stock factory images is the same process described above. However, before locking, there's an additional step to fully revert the device to a clean factory state.

The GrapheneOS factory images flash a non-stock Android Verified Boot key which needs to be erased to fully revert back to a stock device state. After flashing the stock factory images and before locking the bootloader, you should erase the custom Android Verified Boot key to untrust it:

fastboot erase avb_custom_key


[Bu bölüme katkı verebilirsiniz](https://git.oyd.org.tr/oyd/guvenlik)
