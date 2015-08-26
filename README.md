[![Travis-CI Build Status](https://travis-ci.org/davidgohel/rvg.svg?branch=master)](https://travis-ci.org/davidgohel/rvg)

# rvg

`rvg` is an svg graphical driver with options to add tooltips and click actions on 
graphical elements. 

# Installation

    devtools::install_github("davidgohel/rvg")

# Usage

    with( iris, plot( Sepal.Length, Petal.Length , type = "n" ) )
    
    sdata = split( iris, iris$Species )
    
    for(i in names( sdata ) ){
      tempdata = sdata[[i]]
      rvg_tracer_on()
      points(x = tempdata$Sepal.Length , y = tempdata$Petal.Length, pch = 16 )
      ids = rvg_tracer_off()
  
      send_tooltip(as.integer(ids), as.character(tempdata$Petal.Length) )
      send_click(as.integer(ids), paste0("function(){alert('", tempdata$Species,"')}") )
      print(ids)
    }

