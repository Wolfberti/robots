# ------------------------------------------------------------------------
# $Revision: 1.43 $
# $Date: 2006/08/11 23:02:26 $
# ------------------------------------------------------------------------
# Programmer(s): Radu Serban and Aaron Collier @ LLNL
# ------------------------------------------------------------------------
# Copyright (c) 2002, The Regents of the University of California.
# Produced at the Lawrence Livermore National Laboratory.
# All rights reserved.
# For details, see the LICENSE file.
# ------------------------------------------------------------------------
# Process this file with autoconf to produce a configure script.
# ------------------------------------------------------------------------

# Initialize configure
AC_INIT(SUNDIALS, 2.3.0, radu@llnl.gov)

# Display greeting
SUNDIALS_GREETING

# Miscellaneous SUNDIALS initializations
echo "Initialization"
echo "--------------"
echo ""
SUNDIALS_INITIALIZE

# Test enable/disable features
SUNDIALS_ENABLES

# Set C compilation (Required)
echo ""
echo "C Compiler Settings"
echo "-------------------"
echo ""
AC_PROG_CC(cc gcc)
SUNDIALS_SET_CC

# Set Fortran compilation (Optional)
if test "X${FCMIX_ENABLED}" = "Xyes"; then
  echo ""
  echo "Fortran Compiler Settings"
  echo "-------------------------"
  echo ""
  AC_PROG_F77(f77 g77)
  SUNDIALS_SET_F77
fi

# Set MPI support (Optional)
if test "X${MPI_ENABLED}" = "Xyes"; then
  echo ""
  echo "MPI-C Settings"
  echo "--------------"
  echo ""
  SUNDIALS_SET_MPICC
fi
if test "X${MPI_C_COMP_OK}" = "Xyes"; then
  if test "X${FCMIX_ENABLED}" = "Xyes" || test "X${STB_ENABLED}" = "Xyes"; then
    echo ""
    echo "MPI-2 Functionality"
    echo "-------------------"
    echo ""
    SUNDIALS_CHECK_MPI2
  fi
  if test "X${F77_EXAMPLES_ENABLED}" = "Xyes"; then
    echo ""
    echo "MPI-Fortran Settings"
    echo "--------------------"
    echo ""
    SUNDIALS_SET_MPIF77
  fi
fi

# Set examples modules
if test "X${EXAMPLES_ENABLED}" = "Xyes"; then
  echo ""
  echo "Examples"
  echo "--------"
  echo ""
  SUNDIALS_SET_EXAMPLES
fi

# Set Matlab support (optional)
if test "X${STB_ENABLED}" = "Xyes"; then
  echo ""
  echo "Matlab Settings"
  echo "---------------"
  echo ""  
  SUNDIALS_SET_MATLAB  
fi

# Run libtool checks
echo ""
echo "Libtool Settings"
echo "----------------"
echo ""
AC_DISABLE_SHARED
AC_LIBTOOL_WIN32_DLL
AC_PROG_LIBTOOL

# Print a few more lines for configure --help
SUNDIALS_MORE_HELP

# Substitute variables
AC_SUBST(MPICC)
AC_SUBST(MPIF77)
AC_SUBST(MPI_INC_DIR)
AC_SUBST(MPI_LIB_DIR)
AC_SUBST(MPI_LIBS)
AC_SUBST(MPI_FLAGS)
AC_SUBST(FCMIX_ENABLED)
AC_SUBST(FLOAT_TYPE)
AC_SUBST(LIBTOOL_DEPS)
AC_SUBST(F77_MANGLE_MACRO1)
AC_SUBST(F77_MANGLE_MACRO2)
AC_SUBST(F77_CASE)
AC_SUBST(F77_UNDERSCORES)
AC_SUBST(PRECISION_LEVEL)
AC_SUBST(GENERIC_MATH_LIB)
AC_SUBST(F77_MPI_COMM_F2C)
AC_SUBST(F77_LNKR)
AC_SUBST(MPIF77_LNKR)
AC_SUBST(OBJEXT)
AC_SUBST(EXEEXT)
AC_SUBST(STB_PARALLEL_OK)
AC_SUBST(STB_OS)
AC_SUBST(STB_PATH)
AC_SUBST(MATLAB_CMD)
AC_SUBST(MATLAB_CMD_FLAGS)
AC_SUBST(MEXEXT)
AC_SUBST(MEXOPTS)
AC_SUBST(MEXFLAGS)
AC_SUBST(MEXLDADD)
AC_SUBST(SLV_MODULES)
AC_SUBST(EXS_MODULES)
AC_SUBST(STB_MODULES)
AC_SUBST(EXS_INSTDIR)
AC_SUBST(STB_INSTDIR)

# Generate makefiles
echo ""
echo "Create Makefiles and configuration files"
echo "----------------------------------------"
echo ""
SUNDIALS_BUILD_MODULES_LIST
AC_CONFIG_FILES([${SUNDIALS_MAKEFILES}])
AC_CONFIG_FILES([${SUNDIALS_CONFIGFILES}])
AC_OUTPUT

# Display summary
SUNDIALS_REPORT
