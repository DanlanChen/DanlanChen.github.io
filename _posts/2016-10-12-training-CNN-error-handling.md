I have some error handling tricks needing to be logged :

1. When you want to reshape an array with (181,) inside each row is an (512*512) array, you can use

   x = np.array(map(lambda item: np.array(item), x))
   
   alternatively use theano dimensionshuffle(I have not tried yet)
   
2. when you have this problem:

   OverflowError: Range exceeds valid bounds
   
   you need to check if your input image matches the input setting if keras,
   
   try this at the top of your code:
   
   from keras import backend as K
   
   K.set_image_dim_ordering('th')
   
3. when you want to import from __future__ , it should be at the top of your code.
   
   
