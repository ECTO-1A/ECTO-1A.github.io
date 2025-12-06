---
layout: page
title: Current Projects
permalink: /current-projects/
description: An ongoing dump of my current projects. Mainly so I don't forget about them in my never ending list of ideas.
nav: true
comments: false
---

<div class="current-projects-container">
    <div class="projects-header">
        <div class="date-range">June 30th, 2025 - December 31st, 2025</div>
        <div class="last-updated">Last Updated: December 6th, 2025</div>
    </div>

    <div class="projects-content">

        <!-- June  - December 2025 -->
        <div class="day-section">
            <div class="day-header">
            </div>

            <div class="project-item">
                <div class="project-date">November 30th, 2025</div>
                <h3 class="project-title">BPM Meter Using an ESP-32-WROOM</h3>
                <div class="project-description">
                    <p>After recently learning that the ESP-32-WROOM has a built-in ADC (Analog to Digital Converter), I started trying to figure out a good project to use it for. I have some knowledge of ADCs and DACs from my EE days, but I haven't used them outside of the context of an SDR. I figured a simple BPM meter would be a good project to help me learn how to use the ADC in a microcontroller. The device will connect to the RCA output or headphone output from a mixer and use the ADC to measure the voltage of the audio signal. It then uses a simple algorithm to calculate the BPM of the music. It also uses a .96" LCD display to show the BPM and a series of resistors and capacitors to filter the signal and keep the voltage at a safe level for the ADC. Github link, component list, and 3D case model will be added shortly. <br>
                    **This project is still in progress and not based on an existing project. Therefore, I have no idea if this will reliably work. I will update this post when I have done more testing.**</p>
                    <div class="project-image">
                        <img src="/assets/images/bpm.png" alt="BPM Meter" width="450" style="border: 5px solid black; display: block; margin-left: auto; margin-right: auto;">
                    </div>
                </div>
            </div>

            <div class="project-item">
                <div class="project-date">July 6th, 2025</div>
                <h3 class="project-title">Soldering Fume Extractor 3D Build</h3>
                <div class="project-description">
                    <p>I have a bunch of new 80mm PC fans that I have been looking to use for a project.I decided to finally build a 3D printed fume extractor for my soldering station using <a href="https://makerworld.com/en/models/1079138-minimalist-soldering-fume-extractor-80mm-pc-fan?from=search#profileId-1070574" target="_blank">80mm PC Fan Soldering Fume Extractor</a>.</p>
                <div class="project-image">
                        <img src="/assets/images/fume.png" alt="3D Solder Fume Extractor" width="450" style="border: 5px solid black; display: block; margin-left: auto; margin-right: auto;">
                    </div>
                </div>
            </div>

            <div class="project-item">
                <div class="project-date">July 5th, 2025</div>
                <h3 class="project-title">NOTCHACOTCHA Rebuild & Flipper Zero Integration</h3>
                <div class="project-description">
                    <p>Started rebuilding the <a href="https://github.com/hevnsnt/NOTCHACOTCHA" target="_blank">NOTCHACOTCHA</a> repo. Planning to build a Flipper Zero compatible board for laser jamming using the Notchacotcha project as a base. I still need to research the laser radar technology currently deployed by local law enforcement.</p>

                    <div class="project-image">
                        <img src="/assets/images/nc.png" alt="NOTCHACOTCHA Project" width="450" style="border: 5px solid black; display: block; margin-left: auto; margin-right: auto;">
                    </div>

                    <div class="project-media">
                        <h4>Related DEFCON Talk:</h4>
                        <div class="video-container">
                            <iframe src="https://www.youtube.com/embed/vQtLms02PFM?si=DE-qtQCQZOq3md-1" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
                        </div>
                    </div>
                </div>
            </div>

            <div class="project-item">
                <div class="project-date">July 3rd, 2025</div>
                <h3 class="project-title">Lenovo T480 Antenna Modification</h3>
                <div class="project-description">
                    <p>Added external SMA jack to Lenovo T480 to be able to quickly test external antennas. Currently testing <a href="https://www.l-com.com/wireless-antenna-24-ghz-15-dbi-yagi-antenna-12in-n-female-connector" target="_blank">L-Com 2.4 GHz 15 dBi Yagi Antenna</a>.</p>
                </div>
            </div>
        </div>

        <!-- Template for adding new days - COPY THIS SECTION -->
        <!--
        <div class="day-section">
            <div class="day-header">
                <h2 class="day-title">NEW_DATE_HERE</h2>
            </div>

            <div class="project-item">
                <div class="project-date">NEW_DATE_HERE</div>
                <h3 class="project-title">PROJECT_TITLE_HERE</h3>
                <div class="project-description">
                    <p>PROJECT_DESCRIPTION_HERE</p>

                    <!-- Optional: Add image -->
                    <!--
                    <div class="project-image">
                        <img src="/assets/images/IMAGE_NAME.png" alt="PROJECT_ALT_TEXT" width="450" style="border: 5px solid black; display: block; margin-left: auto; margin-right: auto;">
                    </div>
                    -->

                    <!-- Optional: Add video -->
                    <!--
                    <div class="project-media">
                        <h4>Related Video:</h4>
                        <div class="video-container">
                            <iframe src="VIDEO_URL_HERE" title="Video title" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
                        </div>
                    </div>
                    -->
                <!--
                </div>
            </div>
        </div>
        -->

    </div>





    <!-- <p>Head over to My <a href="https://github.com/ECTO-1A">Github repository</a>!</p> -->
</div>

