<p align="center">
<img src="https://github.com/landonbmartin/vm-network/assets/148168629/49b61d23-4240-480f-8ef4-92d6edb9c5ef" heigh="20%" width="20%" alt="Microsoft Azure Logo"/>
</p>

<h1 align = "center">Virtual Machine Network in Microsoft Azure</h1>
This tutorial outlines how to set up a Virtual Machine Network in Microsoft Azure and practicing exercises to observe traffic.

<br>

<h2>Environments and Technologies Used</h2>

<ul>
  <li>Microsoft Azure (Virtual Machines/Compute)</li>
  <li>Microsoft Remote Desktop</li>
</ul>

</br>
<br>

<h2>Operating Systems Used</h2>
<ul>
  <li>Windows 10 (22H2)</li>
  <li>Linux (Ubuntu 20.04)</li>
</ul>

</br>

<h2>List of Prerequisites</h2>
<ol>
  <li>Microsoft Azure Account and Subscription</li>
  <li>Access to Microsoft Remote Desktop Connection</li>
  <ul>
    <li>For MacOS users, follow <a href = "https://www.youtube.com/watch?v=0lllpAhgAJs">this video</a> to use Remote Desktop on Mac</li>
  </ul>
  <li>(OPTIONAL): Use a notepad for typing down username and password information throughout the exercise</li>
</ol>

<h2>Installation Steps</h2>

<h3>Creating the Resource Group and Virtual Machines</h3>

<p>
  <ul>
    <li><b>Resource Group</b></li>
      <ul>
        <li>Through <b>Azure Services</b>, go to <b>Resource Groups</b> to create a Resource Group and name it <b>RG-VM</b>. Take note of the <b>Region</b> of the Resource Group as it will be a factor when setting up the VMs. Once properly filled out, then click on <b>Reivew + Create</b></li>
          <ul>
          <br>
            <img width="700" alt="Setting up RG" src="https://github.com/landonbmartin/vm-network/assets/148168629/1c359909-6dea-4705-906e-fdf866517153">
          </ul>
          </br>
      </ul>
  </ul>
  <ul>
    <li><b>Virtual Machine 1 Using Windows 10</b></li>
    <br>
      <ul>
        <li>Through <b>Azure Services</b>, go to <b>Virtual Machines</b> to create a Virtual Machine. Select the Resource Group created (RG-VM) and name the Virtual Machine <b>VM-1</b>. Make sure the <b>Region</b> is the same as the Resource Group and set the <b>Availability Options</b> to <i>No Infrastructure</i> and <b>Security Type</b> to <i>Standard</i> for this tutorial</li>
        <li>Set the <b>Image</b> (the Operating System) to <i>Windows 10 Pro, Version 22H2, x64 Gen2</i></li>
        <li>The <b>Size</b> selected dictates the general processing power and RAM of our VM. For this tutorial, set it to <i>Standard_E2s_V3</i> which provides 2 virtual CPUs and 16 GBs of RAM</li>
        <ul>
        <br>
          <img width="700" alt="Creating VM-1" src="https://github.com/landonbmartin/vm-network/assets/148168629/da025eb3-e408-45ec-a255-5446b27764d1">
        </ul>
        </br>
        <li>Set the username and password of the VM for logging in and make sure to check the box for licensing agreement</li>
        <ul>
        <br>
          <img width="700" alt="Login   Password" src="https://github.com/landonbmartin/vm-network/assets/148168629/5f73da23-dc20-4eb3-bbf8-3a10d9df3b44">
        </ul>
        </br>
        <li>Go to the <b>Network</b> tab and notice the <b>Virtaul Network</b> created by the Virtual Machine as it should have been made by the Resource Group. It will be made automatically by the Virtual Machine.</li>
        <ul>
        <br>
          <img width="700" alt="Virtual Interface" src="https://github.com/landonbmartin/vm-network/assets/148168629/9db104b7-4f8e-40ae-ac52-eceb3b370cbb">
        </ul>
        </br>
        <li>Then head to the <b>Review + Create</b> and click on <b>Create</b> to deploy your Virtual Machine. Give it a few minutes to fully deploy before moving on.</li>
      </ul>
      <br>
      <li><b>Virtual Machine 2: Using Ubuntu</b></li>
      <br>
      <ul>
        <li>Same process as Virtual Machine 1, but name the VM <b>VM-2</b> and set the Image to <i>Ubuntu Server 20.04 LTS x64 Gen2</i></li>
        <li>Ubuntu by default has Administrator Account authentication as SSH public key, so set it to Password for logging in through Remote Desktop</li>
      <ul>
      <br>
        <img width="700" alt="Ubuntu Login   Password" src="https://github.com/landonbmartin/vm-network/assets/148168629/43280388-7782-46cb-b09b-a205907d35ef">
      </ul>
      </br>
      </li>
      </ul>
    </ul>
  </ul>
</p>

<br />

<h3>Logging into a Virtual Machine using Remote Desktop Connection</h3>

<p>
  <ul>
    <li>Through <b>Azure Services</b>, go to <b>Virtual Machines</b> and select the VM-1 created and click on <b>Connect</b> on the left pannel. To connect to the VM, from this page you can obtain the <b>Public IP Address</b> which we will use to connect via Remote Desktop Connection</li>
    <ul>
    <br>
      <img width="700" alt="VM-1 Connect" src="https://github.com/landonbmartin/vm-network/assets/148168629/9998f399-6fc2-4821-9b55-d1f6ec401773">
    </ul>
    </br>
    <li>Copy the address and paste it into Remote Desktop Connection and click on <b>Connect</b> and log in using the username and password used to set up VM-1</li>
    <ul>
      <li>NOTE: I am currently on MacOS, so this step will look different than when using a PC</li>
    </ul>
    <ul>
    <br>
      <img width="450" alt="Remote Desktop IP Address" src="https://github.com/landonbmartin/vm-network/assets/148168629/4d0e038a-3297-497a-b6bb-59777dfce3e2">
    </ul>
    </br>
    <ul>
      <li>You are now successfully logged into your Windows VM-1!</li>
    </ul>
    <ul>
    <br>
      <img width="1200" alt="Success Remote Login Screen" src="https://github.com/landonbmartin/vm-network/assets/148168629/311258da-458c-4547-893b-b311fbaff13b">
    </ul>
    </br>
  </li>
  </ul>
</p>

<br />

<h2>Observing Traffic in Virtual Machines</h2>

<h3>Download and Install Wireshark</h3>

<p>
  <ul>
    <li>Fist, download <a href="https://www.wireshark.org/download.html">Wireshark</a> in your Windows VM. Downloads may be <i>slow</i> depending on your VM's CPU</li>
    <ul>
    <br>
      <img width="800" alt="Download Wireshark" src="https://github.com/landonbmartin/vm-network/assets/148168629/e42476bd-f4a7-42a5-8943-169b25806f0a">
    </ul>
    </br>
  </ul>
</p>

<br />

<h3>Oberving ICMP (Internet Control Message Protocol) Traffic</h3>

<p>
  <ul>
    <li>Once installed, open Wireshark and start capturing packets (the blue fin icon). In the filter bar, type <b>icmp</b> to filter incoming ICMP packets</li>
    <ul>
    <br>
      <img width="700" alt="icmp filter" src="https://github.com/landonbmartin/vm-network/assets/148168629/622cd83d-948d-4149-b500-0755d2b50963">
    </ul>
    </br>
    <li>Head back to the physical desktop, head to the Microsoft Azure Account to obtain the <b>Private IP Address</b> of VM-2 and copy it</li>
    <ul>
    <br>
      <img width="600" alt="VM-2 Private IP Address" src="https://github.com/landonbmartin/vm-network/assets/148168629/748276ed-7888-463d-a54c-1de49cc38838">
    </ul>
    </br>
    <li>Open up <b>Windows Powershell</b> in VM-1 and in the command line enter <b>ping</b> and the private IP of VM-2. Once done, ICMP packets should now display in Wireshark</li>
    <ul>
    <br>
      <img width="1200" alt="icmp ping VM-2" src="https://github.com/landonbmartin/vm-network/assets/148168629/f0d284f5-92d9-4a7e-a454-c978a2731183">
    </ul>
    </br>
    <li>Now start a perpetual / non-stop ping between the Virtual Machines by entering <b>ping</b> then the private IP of VM-2 followed by <b>-t</b> causing nonstop ICMP packets displaying in Wireshark</li>
    <ul>
    <br>
      <img width="1200" alt="icmp ping VM-2 -t" src="https://github.com/landonbmartin/vm-network/assets/148168629/67989437-b779-4be6-9889-606c5d726d5e">
    </ul>
    </br>
  </ul>
</p>
