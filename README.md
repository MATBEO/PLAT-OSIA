<div align="center">
  <br>

  <a href="https://matbeo.github.io/PLAT-OSIA/">
    <img src="assets/images/All_Color.svg" width="300">
  </a>

  <h1>PLAT-OSIA</h1>
</div>

<div align="left">

<h2><img src="assets/images/visualisation.svg" width="50"> Visualisation</h2>

  <h3>geojson extraction</h3>
  // Define output where to save annotations
def pathOutput = buildFilePath('PATH_TO_SAVE', 'Annotations')
print pathOutput
mkdirs(pathOutput)

// To get all image of the project -> in order to run the scripts on all function (if no project: just getCurrentImageData() and remove the loop)
def project = getProject()

// loop over all image
for (img in project.getImageList()) {
    // get image
    def imageData = img.readImageData()
    // get all annotations
    def rois = getAnnotationObjects().collect {it.getROI()}
    //create a gson instance
    def gson = GsonTools.getInstance(true)
    
    // name of the output file to save
    def name = GeneralTools.getNameWithoutExtension(imageData.getServer().getMetadata().getName())
    def fileOutput = buildFilePath(pathOutput, name)
    println "save annotation: "+fileOutput+".json"
    
    // write (save) the json file
    try (Writer writer = new FileWriter(fileOutput+".json")) {
        gson.toJson(rois, writer);
    }
}

<h2><img src="assets/images/cell.svg" width="50"> Cell</h2>

<h2><img src="assets/images/cluster.svg" width="50"> Cluster</h2>
[cellprofileranalyst](https://cellprofileranalyst.org/)
[cytoflow](https://cytoflow.github.io/)

<h2><img src="assets/images/multiplex.svg" width="50"> Multiplex</h2>

<h2><img src="assets/images/pattern.svg" width="50"> Pattern</h2>

  <h3>detection object / classe</h3>
  <h3>detection pixel</h3>
  <h3>deconvolution couleur IHC pour multiplex</h3>


<h2><img src="assets/images/align.svg" width="50"> Align</h2>

  <h3>Valis</h3>

</div>



