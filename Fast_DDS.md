# Fast DDS and Fast-DDS-Gen Installation [Source Link](https://fast-dds.docs.eprosima.com/en/latest/installation/sources/sources_linux.html)

Even though the installation instructions are brief, it may be exhaustive so please follow the below commands to install Fast-DDS and FastRTPS-Gen for PX4. 

1. Requirements for Fast DDS and FastRTPS-Gen
    - CMake, g++, python3-pip wget git : `sudo apt install cmake g++ python3-pip wget git
      **Note: Install cmake version 3.22.x or higher is required.**
    - SDKMan : 
      - `curl -s "https://get.sdkman.io" | bash`  
      - `source "$HOME/.sdkman/bin/sdkman-init.sh"`  
      - `sdk version` - Should return the version of SDKMan if installed correctly.
   - General Requirements : 
     - `sudo apt install python3-colcon-common-extensions`
     - `sudo apt install openjdk-8-jdk`
     - `pip3 install --user pyros-genmsg`
     - `pip3 install --user jinja2`
     - `pip3 install kconfiglib`
     - `pip3 install --user jsonschema`
     - `pip3 install --user toml`
   - Gradle :
       - `sdk install gradle 7.3`
       - `gradle -v` - Should return the version of Gradle if installed correctly.

2. Fast DDS and FastRTPS-Gen Installation

   **A CMake Global Installation is the only correct installation that works with px4_ros_com. The steps for this is documented in this section**

   ```
   cd 
   mkdir ~/Fast-DDS
   ```
- Foonathan Memory
   ```
   cd ~/Fast-DDS
   git clone https://github.com/eProsima/foonathan_memory_vendor.git
   mkdir foonathan_memory_vendor/build
   cd foonathan_memory_vendor/build
   cmake .. -DCMAKE_INSTALL_PREFIX=/usr/local/ -DBUILD_SHARED_LIBS=ON
   sudo cmake --build . --target install
   ```
- FAST-CDR
   ```
   cd ~/Fast-DDS
   git clone https://github.com/eProsima/Fast-CDR.git
   mkdir Fast-CDR/build
   cd Fast-CDR/build
   cmake ..
   sudo cmake --build . --target install
   ```
- FAST-DDS
   ```
   cd ~/Fast-DDS
   git clone https://github.com/eProsima/Fast-DDS.git
   mkdir Fast-DDS/build
   cd Fast-DDS/build
   cmake ..
   sudo cmake --build . --target install
   ```
- Fast-DDS-Gen
   ```
   cd ~
   git clone --recursive https://github.com/eProsima/Fast-DDS-Gen.git -b v1.0.4
   cd Fast-DDS-Gen
   ./gradlew assemble
   sudo .gradlew install
   ```
- Verify Installtion : 
  - Now to check if correctly installed or not do the following in a new terminal:
   `which fastrtpsgen`
  - It should return something sort of the following: `/usr/local/bin/fastrtpsgen`
  - If it does not return anything, then the installation is not correct. Please check the installation steps again.
