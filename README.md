# Project_In_Gamos

#Abstract: Gamos is a software system for Geant4-based simulation. It comprises a framework, a set of components providing functionality to simulation applications on top of the Geant4 toolkit, and a collection of ready-made applications. It allows to perform Geant4-based simulations using a scripting language, without requiring the writing of C++ code. Moreover, Gamos design allows the extension of the existing functionality through user-supplied C++ classes. The main characteristics of Gamos and its embedded functionality are described. Keywords Monte Carlo methodsGeant4ScriptingPlug-in technology.

/gamos/setParam GmGeometryFromText:FileName linac.geom

/gamos/geometry GmGeometryFromText

/gamos/physicsList GmEMPhysics

/gamos/generator GmGenerator

/gamos/setParam RTPhaseSpaceUA:FileName test

 after target=7, after primary_collimator=78, after flattening_filter=110, after monitor=170, after jaws=450
 
/gamos/setParam RTPhaseSpaceUA:ZStops 7 78 110 170 450 899

/gamos/setParam RTPhaseSpaceUA:KillAfterLastZStop 1

/gamos/setParam RTPhaseSpaceUA:StoreZ 0

/gamos/userAction RTPhaseSpaceUA 

/gamos/userAction GmCountTracksUA 

/gamos/geometry/createRegion targetReg target

/gamos/geometry/createRegion collimatorReg "primary collimator_0"

/gamos/geometry/createRegion filterReg "flattening filter"

/gamos/geometry/createRegion monitorReg monitor

/gamos/geometry/createRegion jawsReg jaws_X jaws_Y

/gamos/physics/setCuts targetReg 10. 0.1

/run/setCut 100.

/run/initialize

/gamos/generator/addSingleParticleSource source e- 6.*MeV

/gamos/generator/directionDist source GmGenerDistDirectionConst 0. 0. 1.

/run/beamOn 100




