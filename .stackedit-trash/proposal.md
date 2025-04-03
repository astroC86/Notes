<!-----

You have some errors, warnings, or alerts. If you are using reckless mode, turn it off to see useful information and inline alerts.
* ERRORs: 0
* WARNINGs: 0
* ALERTS: 1

Conversion time: 0.7 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β44
* Wed Apr 02 2025 22:59:46 GMT-0700 (PDT)
* Source doc: PyLops Propsoal
* This document has images: check for >>>>>  gd2md-html alert:  inline image link in generated source and store images to your server. NOTE: Images in exported zip file from Google Docs may not appear in  the same order as they do in your doc. Please check the images!

----->


<p style="color: red; font-weight: bold">>>>>>  gd2md-html alert:  ERRORs: 0; WARNINGs: 0; ALERTS: 1.</p>
<ul style="color: red; font-weight: bold"><li>See top comment block for details on ERRORs and WARNINGs. <li>In the converted Markdown or HTML, search for inline alerts that start with >>>>>  gd2md-html alert:  for specific instances that need correction.</ul>

<p style="color: red; font-weight: bold">Links to alert messages:</p><a href="#gdcalert1">alert1</a>

<p style="color: red; font-weight: bold">>>>>> PLEASE check and correct alert issues and delete this message and the inline alerts.<hr></p>


**Name and Contact Information \
** **Full Name: **Ziyad AlBanoby \
 **Email: **[ziyadmatt@gmail.com](mailto:ziyadmatt@gmail.com) / [ziyad.albanoby@bsc.es](mailto:ziyad.albanoby@bsc.es)  \
 **Website/GitHub:**[ github.com/](https://github.com/alexjohnson)<span style="text-decoration:underline;">astroC86</span>

**Title ***Towards High Performance NCCL-enabled 2D Partitioned PyLops-MPI Library*

**Biographical Information** \
I am currently pursuing a Master’s degree in Computer Science in Georgia Tech and have over 3 years of experience in high-performance computing and parallel programming. My professional background includes extensive work with Python, MPI, and GPU-accelerated code, complemented by active contributions to different projects in scientific computing. My previous projects have focused on scalable algorithm design and efficient numerical methods, equipping me with the skills and experience necessary to successfully deliver this project and hone them through the guidance of my mentors.


---

**Synopsis \
** This proposal outlines a plan to enhance the PyLops-MPI library by implementing NCCL-enabled collective communication and benchmarking a 2D partitioned design for distributed inverse problem solving. Building on the robust PyLops ecosystem, the project aims to empower researchers and engineers with an efficient tool that scales seamlessly on GPU-accelerated HPC clusters. By addressing key challenges in distributed computations, the project will drive forward both scientific inquiry and practical applications across domains such as geophysics and machine learning.


---

**Deliverables**



1. **2D Partitioned Benchmarking and Enhancement (Goal 2):**
    * Evaluate the performance of the 2D partitioning implementation against the original 1D design.
    * If benchmarks indicate, prototype the 2D SUMMA algorithm to further optimize distributed matrix-matrix multiplication. \
 *Timeline:* Weeks 6–11 \
 *Deliverable Type:* Required

    The current implementation of PyLops-MPI implements the following matrix distribution:


        

<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")
 \


2. **Final Documentation and Tutorials: \
**
    * Comprehensive documentation covering the code, benchmark results, and a tutorial section showcasing use-cases (e.g., Least-squares Migration, Multi-Dimensional Deconvolution).
    * While this will predominantly be performed throughout the project to ensure that there is proper documentation a buffer week is given in case there is a need to modify and iterate over the required documentation. \
 *Timeline:* Week 12 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0OTkyMTk0MDRdfQ==
-->