I have some error handling tricks needing to be logged :

1. When you want to reshape an array with (181,) inside each row is an (512*512) array, you can use

   x = np.array(map(lambda item: np.array(item), x))
   
   alternatively use theano dimensionshuffle(I have not tried yet)
   
2. when you have this problem:

   OverflowError: Range exceeds valid bounds
   
   you need to check if your input image matches the input setting in keras,
   
   try this at the top of your code:
   
   from keras import backend as K
   
   K.set_image_dim_ordering('th')
   
3. when you want to import from __future__ , it should be at the top of your code.

4. when your training loss is nan, you should consider having smaller filter number, shallow network, remove dropout(decrease dropout rate),
you should consider using another optimizer(like rmsprop, increasing its learning rate)

5. when you encounter the problem of" MemoryError: Error allocating 4194893824 bytes of device memory (CNMEM_STATUS_OUT_OF_MEMORY)."
something like that, you should consider using smaller filter number. mainly because the number of your weights parameters are too large.

6. I can not store a array with the first column is (512,512) , the rest columns are scalar into hdf5, and I can not store a dictionary into hdf5, so i just use np.save(), it works.
   
   
