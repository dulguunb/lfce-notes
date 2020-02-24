# Packages
 - RPM package Components
   - Files and Directories
   - Documentation
   - Metadata
   - Versioning
   - Database
   - Verifiable
   - Consistent naming convention
 - RPM package manager
   - package management system
   - used to install/upgrade/remove packages
## Anatomy of RPM package
    rpm -qip <rpm> # querying the rpm
    rpm -qlp <rpm> # inside of the package
    rpm -K <rpm>   # verification of the package
    rpm -ivh <rpm> # - install verbose hashes
    rpm -q <installed_rpm> # query the system
    rpm -qa # query all of the RPMs inistalled in your system
    rpm2cpio <rpm> | cpio -id # extracting a file from the RPM. CPIO is a file
    archive
    rpm -qf /etc/fstab # 
    rpm -qi setup
    rpm -e <installed_rpm> # uninstalls the installed rpm
    rpm -Uwh <rpm> # updates the rpm
    rpm -Vv setup  # changes on the installed RPM
    1-> size
    2-> mode
    3-> md5 checksum
    4-> device number mismatch
    5-> User
    6-> owner
    7-> Time
    8-> File capability
# Package Managers
# Repositories
