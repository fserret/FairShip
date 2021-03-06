# Create a library called "libGen" which includes the source files given in
# the array .
# The extension is already found.  Any number of sources could be listed here.

set(INCLUDE_DIRECTORIES
${CMAKE_SOURCE_DIR}/shipgen
${CMAKE_SOURCE_DIR}/generators
)

set(SYSTEM_INCLUDE_DIRECTORIES
${SYSTEM_INCLUDE_DIRECTORIES}
${PYTHIA8_INCLUDE_DIR}
${SIMPATH}/include
)

include_directories( ${INCLUDE_DIRECTORIES})
include_directories(SYSTEM ${SYSTEM_INCLUDE_DIRECTORIES})

set(LINK_DIRECTORIES
${ROOT_LIBRARY_DIR}
${FAIRROOT_LIBRARY_DIR}
${SIMPATH}/lib
)
 
link_directories( ${LINK_DIRECTORIES})

set(SRCS
Pythia6Generator.cxx
tPythia6Generator.cxx
HNLPythia8Generator.cxx
GenieGenerator.cxx
NuageGenerator.cxx
NtupleGenerator.cxx
MuonBackGenerator.cxx
CosmicsGenerator.cxx
MuDISGenerator.cxx
)

set(LINKDEF  GenLinkDef.h)
set(LIBRARY_NAME ShipGen)

set(DEPENDENCIES  Base ShipData)

GENERATE_LIBRARY()
