# morpheus
[![Build Status](https://travis-ci.com/adubey64/morph.svg?branch=master)](https://travis-ci.com/adubey64/morph)  
A tutorial for CI and code coverage

gcov tutorial

Clone the repository

git clone https://github.com/adubey64/morp.git

Build the tests

cd morph

make

Note that the proper coverage flags have been added to your makefile. Also note that this step generates a set of .gcno files for you.

Run the tests
./runtests

runtests is a perl script which runs the three tests for you. This step generates the .gcda files.
Run gcov on the morph source code

gcov *.cpp

Ignore the system files; we are not responsible for testing them. This will generate our .gcov files
Examine Morpheus_Vector.cpp.gcov and Morpheus_Matrix.cpp.gcov

These are regular text files, so you may use your text editor of choice (vim, emacs, eclipse...or you can just cat the file). Lines that have been tested are marked by the number of times they were executed. Lines that have NOT been tested are preceeded by #####. Dashes denote lines that contain no instructions, such as blank lines or curly braces.

Example: 

      5:   85:bool Matrix::isSymmetric() const

      -:   86:{
      
      5:   87:  if(nrows_ != ncols_)
  
  #####:   88:    return false;
  
      -:   89:
     
     30:   90:  for(int r=0; r<nrows_; r++)
     
      -:   91:  {
    
    150:   92:    for(int c=0; c<ncols_; c++)
    
      -:   93:    {
    
    125:   94:      if(data_[r][c] != data_[c][r])
  
  #####:   95:        return false;
  
      -:   96:    }
      
      -:   97:  }
      
      -:   98:
      
      5:   99:  return true;
      
      -:  100:}
   
Food for thought..

What percentage of Morpheus_Vector.cpp and Morpheus_Matrix.cpp did gcov report was being tested?
How much confidence do you have that my code is correct?
If we had 100% code coverage, would that mean there were no bugs? Why?
Which of the following Vector functions are tested?

Constructor

Destructor

Subscript operator

Const subscript operator

getNumElements

setValue

scale

add

dot

norm1

normInf

norm2

Are the two tests that exist for the Vector class good?

What types of data did I ignore?

What kinds of errors could occur as a result of me ignoring those types of data?

Which of the following Matrix functions are tested?

Constructor

Destructor

Subscript operator

getNumRows

getNumCols

getNumEntries

Matrix-vector multiply

Matrix-matrix multiply

isSymmetric

isUpperTriangular

approxEqual

norm1

normInf

print

Is it sufficient to test the isUpperTriangular function with the identity matrix? Why?

If my tests failed, would it be easy to track down the source of the problem? What could I do to make it easier?
