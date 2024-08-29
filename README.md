
<h1>ZME_MAKE</h1>
<h2>Table of Contents</h2>
<ul>
<li><a href="#build">build</a></li>
<li><a href="#upload">upload</a></li>
<li><a href="#upload-bin">upload_bin</a></li>
<li><a href="#examples">boot</a></li>
<li><a href="#troubleshooting">BoardInfo</a></li>
<li><a href="#faq">eraseNVM</a></li>
<li><a href="#contributing">writeNVM</a></li>
<li><a href="#license">arduino_size</a></li>
<li><a href="#license">arduino_dummy</a></li>
<li><a href="#license">arduino_preproc</a></li>
<li><a href="#license">trace</a></li>
<li><a href="#license">radiotest</a></li>
<li><a href="#license">serialmonitor</a></li>
<li><a href="#pinmap">pinmap</a></li>
</ul>
<h3>Get the list of available commands:</h3>
<blockquote>
<p>zme_make -h</p>
</blockquote>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make -h</pre>
<pre>$ usage: zme_make.py [-h]</pre>
<pre>$                    {build,upload,upload_bin,boot,boardInfo,eraseNVM,writeNVM,dumpNVM,arduino_size,arduino_dummy,arduino_preproc,trace,radiotest,serialmonitor,pinmap} ...</pre>
<pre>$ ZWave>ME make tool for ZUno G2. Version:0.402b18 DBG_MODE:True Welcome :)</pre>
<pre>$ positional arguments:</pre>
<pre>$   {build,upload,upload_bin,boot,boardInfo,eraseNVM,writeNVM,dumpNVM,arduino_size,arduino_dummy,arduino_preproc,trace,radiotest,serialmonitor,pinmap}</pre>
<pre>$     build               Builds a sketch.</pre>
<pre>$     upload              Uploads a sketch to board.</pre>
<pre>$     upload_bin          Uploads a binarie file to board.</pre>
<pre>$     boot                Uploads bootloader.</pre>
<pre>$     boardInfo           Extracts metadata from connected Z-Uno board</pre>
<pre>$     eraseNVM            Erases device NVM data completely.</pre>
<pre>$     writeNVM            Writes data to device NVM memory.</pre>
<pre>$     dumpNVM             Dumps NVM from device.</pre>
<pre>$     arduino_size        Returns memory size allocated by sketch.</pre>
<pre>$     arduino_dummy       Dummy function to meet requirements of Arduino build system.</pre>
<pre>$     arduino_preproc     Makes the right name of sketch.</pre>
<pre>$     trace               Trace packages.</pre>
<pre>$     radiotest           Starts radio test on Z-Uno.</pre>
<pre>$     serialmonitor       Starts serial monitor on defined port.</pre>
<pre>$     pinmap              Creates custom pinmapping for vendor configuration.</pre>
<pre>$ options:</pre>
<pre>$   -h, --help            show this help message and exit</pre>

          </div>
        </div>
      </div>
    <h2>BUILD</h2>
<h3>Description:</h3>
<blockquote>
<p>Build sketch *.ino file before upload</p>
</blockquote>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make build [-h] [-B BUILD_DIR] [-S SOURCE_DIR] [-T TOOLS_PATH] [-lcl LIBCLANG_PATH] [-D DEFINE] [-O OPTIONS] [-C CHIP_NAME] filename</pre>

          </div>
        </div>
      </div>
    <h3>Options:</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>-h, --help</code></td>
<td></td>
<td>Show help message</td>
</tr>
<tr>
<td><code>-B, --build_dir</code></td>
<td>BUILD_DIR</td>
<td>The directory where all precompiled sketch files will be stored.</td>
</tr>
<tr>
<td><code>-S, --source_dir</code></td>
<td>SOURCE_DIR</td>
<td>Directories with the additional files</td>
</tr>
<tr>
<td><code>-T, --tools_path</code></td>
<td>TOOLS_PATH</td>
<td>Path to the directory where GNU Arm Embedded Toolchain is located.</td>
</tr>
<tr>
<td><code>-lcl, --libclang_path</code></td>
<td>LIBCLANG_PATH</td>
<td>Path to the directory where libclang is located.</td>
</tr>
<tr>
<td><code>-D, --define</code></td>
<td>DEFINE</td>
<td>global define flags.</td>
</tr>
<tr>
<td><code>-O, --options</code></td>
<td>OPTIONS</td>
<td>Additional build options, e.g., '-O clean'.</td>
</tr>
<tr>
<td><code>-C, --chip_name</code></td>
<td>CHIP_NAME</td>
<td>Z-Uno chip name. ZGM130S037HGN1 is default for Z-Uno 7 (rev6).</td>
</tr>
<tr>
<td><code>filename</code></td>
<td></td>
<td>Filename of the sketch to be built.</td>
</tr>
</tbody>
</table>
<h3>Example:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make build -B ./build -T /usr/bin -lcl ./libclang -S ./hardware/arduino/zunoG2/cores -S ./hardware/arduino/zunoG2/libraries -S /usr/bin/arm-none-eabi/include -c ZGM130S037HGN1 RadioBlink.ino </pre>
<pre>$           ***** Building sketch:D:\ZunoG2\srcs\RadioBlink.ino *****</pre>
<pre>$           -----------------------------------------------------------------------------------------------</pre>
<pre>$ preprocessing "RadioBlink.ino"           ..............................2) MODERN MCH+</pre>
<pre>$ MODERN MCH+</pre>
<pre>$ preprocessing "RadioBlink.ino"           ..............................                            OK</pre>
<pre>$           Core version: 03.12 Channels:1</pre>
<pre>$           --- Full rebuild because of preprocessing changes!</pre>
<pre>$           Chip depending configuration. Chip:ZGM130S037HGN1</pre>
<pre>$ Gathering project files                  ..............................                            OK</pre>
<pre>$ compiling "em_wdog.c"                    ..............................                            OK</pre>
<pre>$ ......</pre>
<pre>$ ......</pre>
<pre>$ ......</pre>
<pre>$ linking "RadioBlink_ino.elf"             ..............................                            OK</pre>
<pre>$ result "RadioBlink_ino.hex"              ..............................                            OK</pre>
<pre>$ signed "RadioBlink_ino_signed.bin"       ..............................                            OK</pre>
<pre>$           -----------------------------------------------------------------------------------------------</pre>
<pre>$           OTA firmware file: D:\ZunoG2\build\RadioBlink\\RadioBlink_ino_signed.bin</pre>
<pre>$           -----------------------------------------------------------------------------------------------</pre>
<pre>$           Code size:17976 bytes CRC16:cca2 compiled:93 file(s) elapsed:24.645s</pre>

          </div>
        </div>
      </div>
    <p>&lt;/div&gt;</p>
<h2>UPLOAD</h2>
<h3>Options</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>-h, --help</code></td>
<td></td>
<td>Show this help message and exit</td>
</tr>
<tr>
<td><code>-d, --device</code></td>
<td>DEVICE</td>
<td>Device/COM-port name</td>
</tr>
<tr>
<td><code>-B, --build_dir</code></td>
<td>BUILD_DIR</td>
<td>Directory in which all the sketches will be built</td>
</tr>
<tr>
<td><code>-p, --params</code></td>
<td>PARAMS</td>
<td>Optional board configuration parameters</td>
</tr>
<tr>
<td><code>-O, --options</code></td>
<td>OPTIONS</td>
<td>Additional build options. For example, <code>&quot;-O arduino_ide&quot;</code></td>
</tr>
<tr>
<td><code>-fr, --frequency</code></td>
<td><code>{EU, RU, US, IN, HK, CN, JP, KR, IL, MY, ANZ, US_LR, US_LR_BK}</code></td>
<td>Modify frequency setting of the device</td>
</tr>
<tr>
<td><code>-i, --info</code></td>
<td><code>[INFO]</code></td>
<td>Prints board information if selected</td>
</tr>
<tr>
<td><code>-lb, --legacy_baud</code></td>
<td><code>[LEGACY_BAUD]</code></td>
<td>Use legacy baud rate (115200).</td>
</tr>
<tr>
<td><code>-lu, --lic_upload</code></td>
<td>LIC_UPLOAD</td>
<td>Checks ZME server for new license during upload</td>
</tr>
<tr>
<td><code>-c, --clean_nvm</code></td>
<td>CLEAN_NVM</td>
<td>Cleans user and system NVM.</td>
</tr>
<tr>
<td><code>-ub, --ultra_baud</code></td>
<td>ULTRA_BAUD</td>
<td>Use higher baud rate for file uploading</td>
</tr>
<tr>
<td><code>-ne, --no_exentended_sapi</code></td>
<td><code>[NO_EXENTENDED_SAPI]</code></td>
<td>Don't use large SAPI frames. ZME SAPI extension disabled.</td>
</tr>
<tr>
<td><code>-nab, --no_auto_baud</code></td>
<td><code>[NO_AUTO_BAUD]</code></td>
<td>Don't use auto baud detection. Use precise baud rate. Option is useful for devices without <code>#DTR</code> pin.</td>
</tr>
<tr>
<td><code>-a, --address</code></td>
<td>ADDRESS</td>
<td>Custom address for update process</td>
</tr>
</tbody>
</table>
<h3>Example</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make upload RadioBlink.ino -B ./build -p main_pow=50 -p sec=0 -fr EU -d COM9</pre>
<pre>$ Closing port                             ..............................                            OK</pre>
<pre>$ Openning port                            ..............................                            OK</pre>
<pre>$ Syncing with Z-Uno                       ..............................                            OK</pre>
<pre>$ Syncing with Z-Uno                       ..............................                            OK</pre>
<pre>$ --- Sketch addr:00030800</pre>
<pre>$           DEVICE CFG</pre>
<pre>$                 Z-Wave Region:EU</pre>
<pre>$                 Security mode:00 Freqi:00 maxTxDb:32 adjTxDb:00 LRTxDb:00 UART:230400 extra_flags:00</pre>
<pre>$ Writing NVM data                         ..............................                            OK</pre>
<pre>$           Elapsed:1.5935</pre>
<pre>$           Sketch crc16:5d30 size:46f8 (17.74 kB)</pre>
<pre>$ Pushing sketch                           ..............................                            OK</pre>
<pre>$ Closing port                             ..............................                            OK</pre>

          </div>
        </div>
      </div>
    <h3>Example</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make build RadioBlink.ino -B %DIR_OUT%\ -T %CD%\gcc3.10\bin\ -lcl %CD%\libClang -S %CD%\github\hardware\arduino\zunoG2\cores -S %CD%\github\hardware\arduino\zunoG2\libraries -S %CD%\gcc3.10\lib\gcc\arm-none-eabi\10.3.1\include -S %CD%\github\hardware\arduino\zunoG2\cores -S %CD%\github\hardware\arduino\zunoG2\libraries -S %CD%\gcc3.10\lib\gcc\arm-none-eabi\10.3.1\include</pre>
<pre>$           ***** Building sketch:D:\ZunoG2\srcs\RadioBlink.ino *****</pre>
<pre>$           -----------------------------------------------------------------------------------------------</pre>
<pre>$ preprocessing "RadioBlink.ino"           ..............................2) MODERN MCH+</pre>
<pre>$ MODERN MCH+</pre>
<pre>$ preprocessing "RadioBlink.ino"           ..............................                            OK</pre>
<pre>$           Core version: 03.12 Channels:1</pre>
<pre>$           --- Full rebuild because of preprocessing changes!</pre>
<pre>$           Chip depending configuration. Chip:ZGM130S037HGN1</pre>
<pre>$ Gathering project files                  ..............................                            OK</pre>
<pre>$ compiling "em_wdog.c"                    ..............................                            OK</pre>
<pre>$ ......</pre>
<pre>$ ......</pre>
<pre>$ ......</pre>
<pre>$ linking "RadioBlink_ino.elf"             ..............................                            OK</pre>
<pre>$ result "RadioBlink_ino.hex"              ..............................                            OK</pre>
<pre>$ signed "RadioBlink_ino_signed.bin"       ..............................                            OK</pre>
<pre>$           -----------------------------------------------------------------------------------------------</pre>
<pre>$           OTA firmware file: D:\ZunoG2\build\RadioBlink\\RadioBlink_ino_signed.bin</pre>
<pre>$           -----------------------------------------------------------------------------------------------</pre>
<pre>$           Code size:17976 bytes CRC16:cca2 compiled:93 file(s) elapsed:24.645s</pre>

          </div>
        </div>
      </div>
    <h2>UPLOAD BIN</h2>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make upload_bin [-h] [-d DEVICE] [-lb [LEGACY_BAUD]] [-ub ULTRA_BAUD] [-e [EXENTENDED_SAPI]] [-nab [NO_AUTO_BAUD]] [-a ADDRESS] filename</pre>

          </div>
        </div>
      </div>
    <h3>Options</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>-h</code>, <code>--help</code></td>
<td></td>
<td>show this help message and exit</td>
</tr>
<tr>
<td><code>-d</code>, <code>--device</code></td>
<td>DEVICE</td>
<td>Device/COM-port name</td>
</tr>
<tr>
<td><code>-lb</code>, <code>--legacy_baud</code></td>
<td>[LEGACY_BAUD]</td>
<td>Use legacy baudrate (115200).</td>
</tr>
<tr>
<td><code>-ub</code>, <code>--ultra_baud</code></td>
<td>ULTRA_BAUD</td>
<td>Use higher baudrate for file uploading</td>
</tr>
<tr>
<td><code>-e</code>, <code>--exentended_sapi</code></td>
<td>[EXENTENDED_SAPI]</td>
<td>Use large SAPI frames. ZME SAPI extension enabled.</td>
</tr>
<tr>
<td><code>-nab</code>, <code>--no_auto_baud</code></td>
<td>[NO_AUTO_BAUD]</td>
<td>Don't use auto baud detection. Use precise baudrate. Option is useful for devices without #DTR pin.</td>
</tr>
<tr>
<td><code>-a</code>, <code>--address</code></td>
<td>ADDRESS</td>
<td>Custom address for update process</td>
</tr>
<tr>
<td><code>filename</code></td>
<td></td>
<td>Binarie filename</td>
</tr>
</tbody>
</table>
<h3>Example</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make upload_bin -d COM11 .\build\RadioBlink\RadioBlink_ino_signed.bin</pre>
<pre>$ Closing port                             ..............................                            OK</pre>
<pre>$ Openning port                            ..............................                            OK</pre>
<pre>$ Syncing with Z-Uno                       ..............................                            OK</pre>
<pre>$ Syncing with Z-Uno                       ..............................                            OK</pre>
<pre>$ --- Sketch addr:00030800</pre>
<pre>$           DEVICE CFG</pre>
<pre>$                 Z-Wave Region:EU</pre>
<pre>$                 Security mode:00 Freqi:00 maxTxDb:32 adjTxDb:00 LRTxDb:00 UART:230400 extra_flags:00</pre>
<pre>$ Writing NVM data                         ..............................                            OK</pre>
<pre>$           Elapsed:1.5978</pre>
<pre>$           Sketch crc16:5d30 size:46f8 (17.74 kB)</pre>
<pre>$ Pushing sketch                           ..............................                            OK</pre>
<pre>$ Closing port                             ..............................                            OK</pre>

          </div>
        </div>
      </div>
    <h2>BOOT</h2>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make boot [-h] [-c CATALOG] [-f FILENAME] [-d DEVICE] [-i [INFO]] [-lb [LEGACY_BAUD]] [-t [TEST]] [-ub ULTRA_BAUD] [-ne [NO_EXENTENDED_SAPI]] [-nab [NO_AUTO_BAUD]] [-a ADDRESS]</pre>

          </div>
        </div>
      </div>
    <h3>Options</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>-h</code>, <code>--help</code></td>
<td></td>
<td>show this help message and exit</td>
</tr>
<tr>
<td><code>-c</code>, <code>--catalog</code></td>
<td>CATALOG</td>
<td>Bootloader calalogue. Utility asks board information and selects needed bootloader automatically. Recomended mode.</td>
</tr>
<tr>
<td><code>-f</code>, <code>--filename</code></td>
<td>FILENAME</td>
<td>Bootloader filename. This mode is only for experts!</td>
</tr>
<tr>
<td><code>-d</code>, <code>--device</code></td>
<td>DEVICE</td>
<td>Device/COM-port name</td>
</tr>
<tr>
<td><code>-i</code>, <code>--info</code></td>
<td>[INFO]</td>
<td>prints board information if selected</td>
</tr>
<tr>
<td><code>-lb</code>, <code>--legacy_baud</code></td>
<td>[LEGACY_BAUD]</td>
<td>Use legacy baudrate (115200).</td>
</tr>
<tr>
<td><code>-t</code>, <code>--test</code></td>
<td>[TEST]</td>
<td>Test written image by means of read back procedure. Reduce speed. Suitable for flash memory test.</td>
</tr>
<tr>
<td><code>-ub</code>, <code>--ultra_baud</code></td>
<td>ULTRA_BAUD</td>
<td>Use higher baudrate for file uploading</td>
</tr>
<tr>
<td><code>-ne</code>, <code>--no_exentended_sapi</code></td>
<td>[NO_EXENTENDED_SAPI]</td>
<td>Don't use large SAPI frames. ZME SAPI extension disabled.</td>
</tr>
<tr>
<td><code>-nab</code>, <code>--no_auto_baud</code></td>
<td>[NO_AUTO_BAUD]</td>
<td>Don't use auto baud detection. Use precise baudrate. Option is useful for devices without #DTR pin.</td>
</tr>
<tr>
<td><code>-a</code>, <code>--address</code></td>
<td>ADDRESS</td>
<td>Custom address for update process</td>
</tr>
</tbody>
</table>
<h3>Example</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make boot -d com11 -c \hardware\arduino\zunoG2\bootloaders\</pre>
<pre>$ BOOTLOADER</pre>
<pre>$ Closing port                             ..............................                            OK</pre>
<pre>$ Openning port                            ..............................                            OK</pre>
<pre>$ Syncing with Z-Uno                       ..............................                            OK</pre>
<pre>$ Syncing with Z-Uno                       ..............................                            OK</pre>
<pre>$           Using bootloader:\hardware\arduino\zunoG2\bootloaders\zuno_bootloader_HW0704.bin</pre>
<pre>$ Writing NVM data                         ..............................                            OK</pre>
<pre>$           Elapsed:15.1096</pre>
<pre>$ Loading image                            ..............................                            OK</pre>
<pre>$ Rebooting Chip                           ..............................                            OK</pre>
<pre>$ Checking image                           ..............................                            OK</pre>
<pre>$ Waiting for bootloader                   ..............................                            OK</pre>
<pre>$ Closing port                             ..............................                            OK</pre>

          </div>
        </div>
      </div>
    <h2>Board info</h2>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make boardInfo [-h] [-d DEVICE] [-p PARAMS] [-n NIF] [-q QR_CODE] [-lb [LEGACY_BAUD]] [-lu LIC_UPLOAD] [-ub ULTRA_BAUD] [-nab [NO_AUTO_BAUD]] [-dp DUMP_PRODUCT]</pre>

          </div>
        </div>
      </div>
    <h3>Options</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>-h</code>, <code>--help</code></td>
<td></td>
<td>show this help message and exit</td>
</tr>
<tr>
<td><code>-d</code>, <code>--device</code></td>
<td>DEVICE</td>
<td>Device/COM-port name</td>
</tr>
<tr>
<td><code>-p</code>, <code>--params</code></td>
<td>PARAMS</td>
<td>Optional board configuration parameters</td>
</tr>
<tr>
<td><code>-n</code>, <code>--nif</code></td>
<td>NIF</td>
<td>Sends a set of NIF frames via radio</td>
</tr>
<tr>
<td><code>-q</code>, <code>--qr_code</code></td>
<td>QR_CODE</td>
<td>Prints QR-code to selected image file.</td>
</tr>
<tr>
<td><code>-lb</code>, <code>--legacy_baud</code></td>
<td>[LEGACY_BAUD]</td>
<td>Use legacy baudrate (115200).</td>
</tr>
<tr>
<td><code>-lu</code>, <code>--lic_upload</code></td>
<td>LIC_UPLOAD</td>
<td>Checks ZME server for new license during upload</td>
</tr>
<tr>
<td><code>-ub</code>, <code>--ultra_baud</code></td>
<td>ULTRA_BAUD</td>
<td>Use higher baudrate for file uploading</td>
</tr>
<tr>
<td><code>-nab</code>, <code>--no_auto_baud</code></td>
<td>[NO_AUTO_BAUD]</td>
<td>Don't use auto baud detection. Use precise baudrate. Option is useful for devices without #DTR pin.</td>
</tr>
<tr>
<td><code>-dp</code>, <code>--dump_product</code></td>
<td>DUMP_PRODUCT</td>
<td>Dumps product Z-Wave metadata into specified json-file. You'll able to use this file for SmartStart QR-code production in zme_prog7 utility.</td>
</tr>
</tbody>
</table>
<h3>Example</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make boardInfo -d com11</pre>
<pre>$ BOARD INFO</pre>
<pre>$ Closing port                             ..............................                            OK</pre>
<pre>$ Openning port                            ..............................                            OK</pre>
<pre>$ Syncing with Z-Uno                       ..............................                            OK</pre>
<pre>$ Syncing with Z-Uno                       ..............................                            OK</pre>
<pre>$           ------------------------------------------------------------------------------------</pre>
<pre>$                                         Z-Uno board information</pre>
<pre>$           ------------------------------------------------------------------------------------</pre>
<pre>$           FIRMWARE</pre>
<pre>$                  VERSION:               03.12</pre>
<pre>$                  BUILD_SEQUENCE:        00004328</pre>
<pre>$                  BUILD_DATETIME:        2024-07-29T20:53:31(MSK)</pre>
<pre>$                  SUPPORTED_HWREV:       0704</pre>
<pre>$                  KEY HASH:              8e19cc54</pre>
<pre>$                  SE VERSION:            00000000</pre>
<pre>$           LIMITS</pre>
<pre>$                  CODE:  456704 Bytes</pre>
<pre>$                  RAM:   16384 Bytes</pre>
<pre>$           HARDWARE</pre>
<pre>$                  CHIP_FAMILY:    ZGM13 Module (00)</pre>
<pre>$                  CHIP_TYPE:      ZGM130S037HGN1 (02)</pre>
<pre>$                  CHIP_UID:       84 2E 14 FF FE 6A 28 9B</pre>
<pre>$                  PROD_TIME:      2024-05-29T16:11:10(MSK)</pre>
<pre>$                  PROD_SN:        2</pre>
<pre>$                  LOCK:           UNLOCKED</pre>
<pre>$                  EXT NVM:        0</pre>
<pre>$           LICENSE</pre>
<pre>$                  SUB_VENDOR:    0000</pre>
<pre>$                  BITMASK:       0000000000000020</pre>
<pre>$                  FEATURES:      [LONG_RANGE]</pre>
<pre>$                  CRC16:         ff91</pre>
<pre>$           NETWORK</pre>
<pre>$                  HOMEID:        f65b8f92</pre>
<pre>$                  NODEID:        9</pre>
<pre>$           SECURITY</pre>
<pre>$                 S2 DSK:         46593-06376-32171-65094-27264-38172-33243-09871</pre>
<pre>$                                 _____</pre>
<pre>$                 S2 PIN:         46593</pre>
<pre>$                 QR-Code:        90010369013146593063763217165094272643817233243098710010040960179202200027700528000010078008030010403005</pre>
<pre>$           ------------------------------------------------------------------------------------</pre>
<pre>$           SKETCH</pre>
<pre>$            -- NO VALID SKETCH --</pre>
<pre>$           DEVICE CFG</pre>
<pre>$                 Z-Wave Region:EU</pre>
<pre>$                 Security mode:00 Freqi:00 maxTxDb:32 adjTxDb:00 LRTxDb:00 UART:230400 extra_flags:00</pre>
<pre>$ Reseting chip                            ..............................                            OK</pre>
<pre>$ DONE</pre>

          </div>
        </div>
      </div>
    <h2>Erase NVM</h2>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make eraseNVM [-h] [-d DEVICE] [-r [RAW_MODE]] [-a ADDRESS] [-s SIZE] [-ub ULTRA_BAUD] [-nab [NO_AUTO_BAUD]]</pre>

          </div>
        </div>
      </div>
    <h3>Options</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>-h</code>, <code>--help</code></td>
<td></td>
<td>Show this help message and exit</td>
</tr>
<tr>
<td><code>-d</code>, <code>--device</code></td>
<td>DEVICE</td>
<td>Device/COM-port name</td>
</tr>
<tr>
<td><code>-r</code>, <code>--raw_mode</code></td>
<td>[RAW_MODE]</td>
<td>Big endian/Small endian conversion</td>
</tr>
<tr>
<td><code>-a</code>, <code>--address</code></td>
<td>ADDRESS</td>
<td>Address of memory in hexadecimals</td>
</tr>
<tr>
<td><code>-s</code>, <code>--size</code></td>
<td>SIZE</td>
<td>Size of memory area to dump</td>
</tr>
<tr>
<td><code>-ub</code>, <code>--ultra_baud</code></td>
<td>ULTRA_BAUD</td>
<td>Use higher baudrate for file uploading</td>
</tr>
<tr>
<td><code>-nab</code>, <code>--no_auto_baud</code></td>
<td>[NO_AUTO_BAUD]</td>
<td>Don't use auto baud detection. Use precise baudrate. Option is useful for devices without #DTR pin.</td>
</tr>
</tbody>
</table>
<h3>Example</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make eraseNVM -d com11</pre>
<pre>$ NVM Erase</pre>
<pre>$ Closing port                             ..............................                            OK</pre>
<pre>$ Openning port                            ..............................                            OK</pre>
<pre>$ Syncing with Z-Uno                       ..............................                            OK</pre>
<pre>$ Syncing with Z-Uno                       ..............................                            OK</pre>
<pre>$ Closing port                             ..............................                            OK</pre>
<pre>$ DONE</pre>

          </div>
        </div>
      </div>
    <h2>WRITE NVM</h2>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            
          </div>
        </div>
      </div>
    <h3>Options</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
</table>
<h2>DUMP NVM</h2>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            
          </div>
        </div>
      </div>
    <h3>Options</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
</table>
<h2>ARDUINO SIZE</h2>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make arduino_size [-h] [-B BUILD_DIR] filename</pre>

          </div>
        </div>
      </div>
    <h3>Options</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>-h</code>, <code>--help</code></td>
<td></td>
<td>show this help message and exit</td>
</tr>
<tr>
<td><code>-B</code>, <code>--build_dir</code></td>
<td>BUILD_DIR</td>
<td>Directory in which all the sketches will be built</td>
</tr>
</tbody>
</table>
<h3>Example:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make arduino_size -B D:\build\RadioBlink RadioBlink.ino </pre>
<pre>$ .text   18168</pre>
<pre>$ .ram    1524</pre>

          </div>
        </div>
      </div>
    <h2>ARDUINO DUMMY</h2>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            
          </div>
        </div>
      </div>
    <h3>Options</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
</table>
<h2>ARDUINO PREPROC</h2>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            
          </div>
        </div>
      </div>
    <h3>Options</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
</table>
<h2>с</h2>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ $ zme_make trace [-h] [-d DEVICE] [-b BAUDRATE] [-fr {EU,US,ANZ,HK,MY,IN,IL,RU,CN,US_LR,US_LR_BK,EU_LR,JP,KR,FK}] [-tp TX_POWER] [-t {MODEM,PTI}] [-i INPUT] [-f FILTER] [-ir [INPUT_REENCODE]] [-o OUTPUT]</pre>
<pre>$                          [-mp MAX_PACKAGES] [-mt MAX_TIME] [-p PROFILE] [-s SEND] [-r {off,payload,full,complex,hex_app}] [-dt {auto,z-uno,sapi}] [-nab [NO_AUTO_BAUD]]</pre>

          </div>
        </div>
      </div>
    <h3>Options</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>-h</code>, <code>--help</code></td>
<td></td>
<td>show this help message and exit</td>
</tr>
<tr>
<td><code>-d</code>, <code>--device</code></td>
<td></td>
<td>Device file (UNIX) or COM-port (WINDOWS)</td>
</tr>
<tr>
<td><code>-b</code>, <code>--baudrate</code></td>
<td>BAUDRATE</td>
<td>Device's baudrate.</td>
</tr>
<tr>
<td><code>-fr</code>, <code>--frequency</code></td>
<td>{EU, US, ANZ, HK, MY, IN, IL, RU, CN, US_LR, US_LR_BK, EU_LR, JP, KR, FK}</td>
<td>Defines Z-Wave region (for MODEM mode ONLY).</td>
</tr>
<tr>
<td><code>-tp</code>, <code>--tx_power</code></td>
<td>TX_POWER</td>
<td>Defines Z-Wave tx power (for MODEM mode ONLY).</td>
</tr>
<tr>
<td><code>-t</code>, <code>--transport_type</code></td>
<td>{MODEM,PTI}</td>
<td>Select needed transport protocol</td>
</tr>
<tr>
<td><code>-i</code>, <code>--input</code></td>
<td>INPUT</td>
<td>Imports specified file instead of device. Utility supports *.rtp, *.json, *.zlf files.</td>
</tr>
<tr>
<td><code>-f</code>, <code>--filter</code></td>
<td>FILTER</td>
<td>Filters data.</td>
</tr>
<tr>
<td><code>-ir</code>, <code>--input_reencode</code></td>
<td>[INPUT_REENCODE]</td>
<td>Reencodes incoming data during print</td>
</tr>
<tr>
<td><code>-o</code>, <code>--output</code></td>
<td>OUTPUT</td>
<td>Dumps all received packages to specified file</td>
</tr>
<tr>
<td><code>-mp</code>, <code>--max_packages</code></td>
<td>MAX_PACKAGES</td>
<td>Stops when the packet counter reaches the set value</td>
</tr>
<tr>
<td><code>-mt</code>, <code>--max_time</code></td>
<td>MAX_TIME</td>
<td>Stops after reaching the specified time interval</td>
</tr>
<tr>
<td><code>-p</code>, <code>--profile</code></td>
<td>PROFILE</td>
<td>JSON file with Z-Wave protocol descriptions.</td>
</tr>
<tr>
<td><code>-s</code>, <code>--send</code></td>
<td>SEND</td>
<td>Sends Z-Wave message. You can send multiple messages using this parameter multiple times. You can use several modes to send messages: RAW, APP, SLP. RAW mode sends the Z-Wave message as is, everything written in the second parameter is sent without additional checks. Format: -s RAW,CH,HEXSTR Where CH is the channel through which the message is sent (0 - 100 kbps, 1 - 40kbps, 2-9.6kbps), HEXSTR is a hexadecimal string. Example: -s RAW,0,AABBCCDD00010203 sends arbitrary data via a 100 kilobit (#0) channel. APP mode generates an application-level Z-Wave package based on data provided by the user separated by commas. The user must specify the channel, home id, source node_id, destination node_id, command class.command and further parameters of this Z-Wave command, in addition, optional parameters can be specified by enumeration. Format: -s APP,CH,HOMEID,SRC_NODE_ID,DST_NODE_ID,CC.CMD,[Param1,...,ParamN][,Option1=Value1,...,OptionM=ValueM] Where: CH is the channel through which the message is sent (0 - 100 kbps, 1 - 40kbps, 2-9.6kbps), HOMEID is address of needed Z-Wave Network, SRC_NODE_ID - address of sender (fake address in this case), SRC_NODE_ID - address of receiver (fake address in this case). If you use a dot in the address, the message will be wrapped in a Multichannel, CC.CMD - Application level command class and its  command. You can use text or hexadecimal format. For example BASIC.SET or equivalently 2001. Param1...ParamN - parameters of desired command, Option1.. ptionM - options of encoder Examples: -s APP,1,FD0F1122,1,50,SWITCH_BINARY.SET,255 - sends SwitchBinary.set(255) to NodeID 50 in FD0F1122 network -s APP,1,FD0F1122,1,50,SWITCH_BINARY.SET,0,is_ack=True - sends SwitchBinary.set(0) to NodeID 50 in FD0F1122 network and requests ACK from this node -s APP,1,FD0F1122,1,50,SWITCH_BINARY.SET,0,is_ack=True,crc16_encap=True - sends SwitchBinary.set(0) to NodeID 50 in FD0F1122 network and requests ACK from this node and wraps payload to crc16 CommandClass SLP mode simply inserts a delay between the previous and next packet. Format: -s SLP,time_in_seconds Example: -s APP,1,FD0F1122,1,50,SWITCH_BINARY.SET,255,is_ack=True -s SLP,20.0 -s APP,1,FD0F1122,1,50,SWITCH_BINARY.SET,0,is_ack=True Sends a BinarySwitch.Set(255) then waits 20 seconds and sends a Binary BinarySwitch.Set(0) -r {off,payload,full,complex,hex_app}, --raw_mode {off,payload,full,complex,hex_app} Defines the raw data printing mode. &quot;off&quot; - data is disabled, &quot;payload&quot; - only payload (starting from the application-level command class), &quot;full&quot; - print the entire package as it is, &quot;complex&quot; - print the package and then its payload in parentheses, &quot;hex_app&quot; - hexadecimal payload data only -dt {auto,z-uno,sapi}, --device_type {auto,z-uno,sapi} Selects device type</td>
</tr>
<tr>
<td><code>-nab</code>, <code>--no_auto_baud</code></td>
<td>[NO_AUTO_BAUD]</td>
<td>Don't use auto baud detection. Use precise baudrate. Option is useful for devices without #DTR pin.</td>
</tr>
</tbody>
</table>
<h2>RADIO TEST</h2>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            
          </div>
        </div>
      </div>
    <h3>Options</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
</table>
<h2>SERIAL MONITOR</h2>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            
          </div>
        </div>
      </div>
    <h3>Options</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
</table>
<h2>PINMAP</h2>
<h3>Usage:</h3>

      <div>
        <div style="background-color: #1e1e1e; border-radius: 8px; color: #e6e6e6; font-size: 16px; line-height: 1.5; width: 100%; padding: 20px; box-shadow: 0 8px 16px rgba(0, 0, 0, 0.2); overflow-x: auto;">
          <div style="display: flex; justify-content: flex-start; gap: 8px; margin-bottom: 10px;">
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ff605c;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #ffbd44;"></span>
            <span style="width: 12px; height: 12px; border-radius: 50%; display: inline-block; background-color: #00ca4e;"></span>
          </div>
          <div style="background-color: #000; padding: 15px; border-radius: 4px; color: #00ff00; overflow-x: auto;">
            <pre>$ zme_make.py pinmap [-h] [-c {ZGM130S037HGN1,ZGM230SB27HGN,ZGM230SA27HGN,EFR32ZG23B020F512IM48,EFR32ZG23B010F512IM48,EFR32ZG23A010F512GM40}] [-s [SWD_AS_UART]] [-v VENDOR] [-pt PRODUCTTYPE_ID] [-pi PRODUCT_ID] [-pow POWER_MAX] [-efr EXTERNAL_MEMORY_FREQUENCY] [-m MAP] [-l [PINNAME_LIST]]</pre>

          </div>
        </div>
      </div>
    <h3>Options:</h3>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
</table>
<table>
<thead>
<tr>
<th>Option</th>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>-h, --help</code></td>
<td></td>
<td>Show help message</td>
</tr>
<tr>
<td><code>-c</code></td>
<td>{chip_name}</td>
<td>Selects the chip model</td>
</tr>
<tr>
<td><code>-s, --swd_as_uart </code></td>
<td>SWD_AS_UART</td>
<td>Maps SWD pins to SAPI UART. SWDCLC=TX SWDIO=RX SWDO=DBG_TX</td>
</tr>
<tr>
<td><code>-v, --vendor</code></td>
<td>VENDOR</td>
<td>set Z-Wave Vendor ID</td>
</tr>
<tr>
<td><code>-pt, --producttype_id </code></td>
<td>PRODUCTTYPE_ID</td>
<td>set Z-Wave Product Type ID</td>
</tr>
<tr>
<td><code>-pi, --product_id</code></td>
<td>PRODUCT_ID</td>
<td>set Z-Wave Product ID</td>
</tr>
<tr>
<td><code>-pow, --power_max</code></td>
<td>POWER_MAX</td>
<td>Maximum power of the end device</td>
</tr>
<tr>
<td><code>-efr, --external_memory_frequency</code></td>
<td>EXTERNAL_MEMORY_FREQUENCY</td>
<td>Frequency of the external NVM chip SPI interface in MHz</td>
</tr>
<tr>
<td><code>-m, --map</code></td>
<td>MAP</td>
<td>Maps selected pins. Format:   <code>&lt;pinname&gt;=&lt;port&gt;&lt;pin&gt;,..,&lt;pinname&gt;=&lt;port&gt;&lt;pin&gt;</code>,<code>#&lt;zunopinnumber&gt;=&lt;port&gt;&lt;pin&gt;</code>. Where <code>&lt;port&gt;</code>=A..F - the cortex port, pin = 0..15</td>
</tr>
<tr>
<td><code>-l , --pinname_list</code></td>
<td></td>
<td>Outputs all pin names</td>
</tr>
</tbody>
</table>
<p>&lt;details&gt;&lt;summary&gt;</p>
<h4>Default mapping of defined names and Pin number</h4>
<p>&lt;/summary&gt;</p>
<h3>PWM pins name</h3>
<blockquote>
<p><em>analogWrite() Writes an analog value (PWM wave) to a pin. Can be used to light a LED varying brightnesses or drive a motor at various speeds</em></p>
</blockquote>
<table>
<thead>
<tr>
<th>Name</th>
<th>Pin number #</th>
</tr>
</thead>
<tbody>
<tr>
<td>PWM1</td>
<td>13</td>
</tr>
<tr>
<td>PWM2</td>
<td>14</td>
</tr>
<tr>
<td>PWM3</td>
<td>15</td>
</tr>
<tr>
<td>PWM4</td>
<td>16</td>
</tr>
</tbody>
</table>
<h3>ADC</h3>
<blockquote>
<p><em>analogRead()
Reads the value from the specified analog pin. The Z-Uno board contains a 4 channel, 10-bit analog to digital converter. This means that it will map input voltages between 0 and Vcc (about 3 V) into integer values between 0 and 1023.</em></p>
</blockquote>
<table>
<thead>
<tr>
<th>Name</th>
<th>Pin number #</th>
</tr>
</thead>
<tbody>
<tr>
<td>A0</td>
<td>3</td>
</tr>
<tr>
<td>A1</td>
<td>4</td>
</tr>
<tr>
<td>A2</td>
<td>5</td>
</tr>
<tr>
<td>A3</td>
<td>6</td>
</tr>
</tbody>
</table>
<h3>Serial</h3>
<blockquote>
<p><em>Serial() Used for communication between the Z-Uno board and another microcontroller or a computer via UART or USB.</em></p>
</blockquote>
<h3>Serial0</h3>
<table>
<thead>
<tr>
<th>Name</th>
<th>Pin number #</th>
</tr>
</thead>
<tbody>
<tr>
<td>RX0</td>
<td>25</td>
</tr>
<tr>
<td>TX0</td>
<td>24</td>
</tr>
</tbody>
</table>
<h3>Serial1</h3>
<table>
<thead>
<tr>
<th>Name</th>
<th>Pin number #</th>
</tr>
</thead>
<tbody>
<tr>
<td>RX1</td>
<td>8</td>
</tr>
<tr>
<td>TX1</td>
<td>7</td>
</tr>
</tbody>
</table>
<h3>Serial</h3>
<blockquote>
<p><em>default serial port for connect to PC (upload sketch and update device)</em></p>
</blockquote>
<table>
<thead>
<tr>
<th>Name</th>
<th>Pin number #</th>
</tr>
</thead>
<tbody>
<tr>
<td>RX2</td>
<td>27</td>
</tr>
<tr>
<td>TX2</td>
<td>26</td>
</tr>
</tbody>
</table>
<h3>SPI0</h3>
<table>
<thead>
<tr>
<th>Name</th>
<th>Pin number #</th>
</tr>
</thead>
<tbody>
<tr>
<td>SCK</td>
<td>0</td>
</tr>
<tr>
<td>MISO</td>
<td>1</td>
</tr>
<tr>
<td>MOSI</td>
<td>2</td>
</tr>
<tr>
<td>SS</td>
<td>8</td>
</tr>
</tbody>
</table>
<h3>SPI1</h3>
<table>
<thead>
<tr>
<th>Name</th>
<th>Pin number #</th>
</tr>
</thead>
<tbody>
<tr>
<td>SCK2</td>
<td>3</td>
</tr>
<tr>
<td>MISO2</td>
<td>4</td>
</tr>
<tr>
<td>MOSI2</td>
<td>7</td>
</tr>
<tr>
<td>SS2</td>
<td>8</td>
</tr>
<tr>
<td>&lt;/div&gt;&lt;/details&gt;</td>
<td></td>
</tr>
</tbody>
</table>
<p>&lt;details&gt;&lt;summary&gt;</p>
<h4>Default mapping Pin number # ZUNO</h4>
<p>&lt;/summary&gt;</p>
<p>&lt;details&gt;&lt;summary&gt;ZGM230S* (Z-Wave 800 Series chips)&lt;/summary&gt;</p>
<table>
<thead>
<tr>
<th style="text-align:center">Pin number #</th>
<th style="text-align:center">Chip port</th>
<th style="text-align:center">Defined pin name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center">0</td>
<td style="text-align:center">PC00</td>
<td style="text-align:center">SCK</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">1</td>
<td style="text-align:center">PC01</td>
<td style="text-align:center">MISO</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">2</td>
<td style="text-align:center">PC02</td>
<td style="text-align:center">MOSI</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">3</td>
<td style="text-align:center">PD00</td>
<td style="text-align:center">A0 / SCK2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">4</td>
<td style="text-align:center">PA06</td>
<td style="text-align:center">A1 / MISO2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">5</td>
<td style="text-align:center">PA05</td>
<td style="text-align:center">A2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">6</td>
<td style="text-align:center">PC04</td>
<td style="text-align:center">A3</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">7</td>
<td style="text-align:center">PA09</td>
<td style="text-align:center">TX1 / MOSI2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">8</td>
<td style="text-align:center">PA08</td>
<td style="text-align:center">RX1 / SS / SS2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">9</td>
<td style="text-align:center">PC09</td>
<td style="text-align:center">SCL</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">10</td>
<td style="text-align:center">PA10</td>
<td style="text-align:center">SDA</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">11</td>
<td style="text-align:center">PD03</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">12</td>
<td style="text-align:center">PC05</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">13</td>
<td style="text-align:center">PB01</td>
<td style="text-align:center">PWM1</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">14</td>
<td style="text-align:center">PB03</td>
<td style="text-align:center">PWM2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">15</td>
<td style="text-align:center">PB04</td>
<td style="text-align:center">PWM3</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">16</td>
<td style="text-align:center">PB05</td>
<td style="text-align:center">PWM4</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">17</td>
<td style="text-align:center">PB06</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">18</td>
<td style="text-align:center">PD01</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">19</td>
<td style="text-align:center">PC06</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">20</td>
<td style="text-align:center">PC02</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">21</td>
<td style="text-align:center">PC03</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">22</td>
<td style="text-align:center">PC04</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">23</td>
<td style="text-align:center">PD02</td>
<td style="text-align:center">BTN / SCL1</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">24</td>
<td style="text-align:center">PA03</td>
<td style="text-align:center">TX0</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">25</td>
<td style="text-align:center">PA04</td>
<td style="text-align:center">RX0 / SDA1</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">26</td>
<td style="text-align:center">PA2</td>
<td style="text-align:center">TX2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">27</td>
<td style="text-align:center">PA1</td>
<td style="text-align:center">RX2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">28</td>
<td style="text-align:center">PB00</td>
<td style="text-align:center"></td>
<td>Pin for service green led</td>
</tr>
<tr>
<td style="text-align:center">29</td>
<td style="text-align:center">PB01</td>
<td style="text-align:center"></td>
<td>Pin for service red led</td>
</tr>
</tbody>
</table>
<p>&lt;/div&gt;&lt;/details&gt;</p>
<p>&lt;details&gt;&lt;summary&gt;ZGM130S* (Z-Wave 700 Series chips)&lt;/summary&gt;</p>
<table>
<thead>
<tr>
<th style="text-align:center">Pin number #</th>
<th style="text-align:center">Chip port</th>
<th style="text-align:center">Defined pin name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:center">0</td>
<td style="text-align:center">PC00</td>
<td style="text-align:center">SCK</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">1</td>
<td style="text-align:center">PC01</td>
<td style="text-align:center">MISO</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">2</td>
<td style="text-align:center">PC02</td>
<td style="text-align:center">MOSI</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">3</td>
<td style="text-align:center">PD00</td>
<td style="text-align:center">A0 / SCK2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">4</td>
<td style="text-align:center">PA06</td>
<td style="text-align:center">A1 / MISO2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">5</td>
<td style="text-align:center">PA05</td>
<td style="text-align:center">A2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">6</td>
<td style="text-align:center">PC04</td>
<td style="text-align:center">A3</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">7</td>
<td style="text-align:center">PA09</td>
<td style="text-align:center">TX1 / MOSI2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">8</td>
<td style="text-align:center">PA08</td>
<td style="text-align:center">RX1 / SS / SS2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">9</td>
<td style="text-align:center">PC09</td>
<td style="text-align:center">SCL</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">10</td>
<td style="text-align:center">PA10</td>
<td style="text-align:center">SDA</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">11</td>
<td style="text-align:center">PD03</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">12</td>
<td style="text-align:center">PC05</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">13</td>
<td style="text-align:center">PB01</td>
<td style="text-align:center">PWM1</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">14</td>
<td style="text-align:center">PB03</td>
<td style="text-align:center">PWM2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">15</td>
<td style="text-align:center">PB04</td>
<td style="text-align:center">PWM3</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">16</td>
<td style="text-align:center">PB05</td>
<td style="text-align:center">PWM4</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">17</td>
<td style="text-align:center">PB06</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">18</td>
<td style="text-align:center">PD01</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">19</td>
<td style="text-align:center">PC06</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">20</td>
<td style="text-align:center">PC02</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">21</td>
<td style="text-align:center">PC03</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">22</td>
<td style="text-align:center">PC04</td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">23</td>
<td style="text-align:center">PD02</td>
<td style="text-align:center">BTN / SCL1</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">24</td>
<td style="text-align:center">PA03</td>
<td style="text-align:center">TX0</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">25</td>
<td style="text-align:center">PA04</td>
<td style="text-align:center">RX0 / SDA1</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">26</td>
<td style="text-align:center">PA2</td>
<td style="text-align:center">TX2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">27</td>
<td style="text-align:center">PA1</td>
<td style="text-align:center">RX2</td>
<td></td>
</tr>
<tr>
<td style="text-align:center">28</td>
<td style="text-align:center">PB00</td>
<td style="text-align:center">ledg</td>
<td>Pin for service green led</td>
</tr>
<tr>
<td style="text-align:center">29</td>
<td style="text-align:center">PB01</td>
<td style="text-align:center">ledr</td>
<td>Pin for service service red led</td>
</tr>
<tr>
<td style="text-align:center">&lt;/div&gt;</td>
<td style="text-align:center"></td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">&lt;/details&gt;</td>
<td style="text-align:center"></td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">&lt;/div&gt;</td>
<td style="text-align:center"></td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">&lt;/details&gt;</td>
<td style="text-align:center"></td>
<td style="text-align:center"></td>
<td></td>
</tr>
<tr>
<td style="text-align:center">&lt;/div&gt;</td>
<td style="text-align:center"></td>
<td style="text-align:center"></td>
<td></td>
</tr>
</tbody>
</table>
