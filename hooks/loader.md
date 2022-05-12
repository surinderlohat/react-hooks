# Use Loader

User Loader Hook helps in showing the loader while making any API call or async operations.
this hook will help in managing seprate loaders for api calls.

## Features
1. Useful hooks for react js.
2. Open source Free to use.

## How to use
```sh
import { FC } from 'react';
import { Box, Button } from '@mui/material';
import { useLoader } from '@surinderlohat/react-hooks';

const LoaderHook: FC = () => {
  const loader = useLoader();
  const otherLoader = useLoader();

  // Mock First API Call
  const fetchDataFromApi = () => {
    loader.showLoader();
    setTimeout(() => loader.hideLoader(), 5000);
  };

  // Mock Second API Call
  const fetchDataFromApiTwo = () => {
    otherLoader.showLoader();
    setTimeout(() => otherLoader.hideLoader(), 5000);
  };

  return (
    <Box sx={{ display: 'flex', justifyContent: 'center' }}>
      <Box>
        {loader.isLoading && 'Loading data from First call'}
        <Button onClick={fetchDataFromApi}>Load Data</Button>
      </Box>

      <Box>
        {otherLoader.isLoading && 'Loading data from Second call'}
        <Button onClick={fetchDataFromApiTwo}>Load Data for Second call</Button>
      </Box>
    </Box>
  );
};

export default LoaderHook;

```
## Like This Hook ? 
We have more for your:
- [Use Pagination](https://github.com/surinderlohat/react-hooks/hooks/pagination)

## About Me
- [Surinder Lohat](https://github.com/surinderlohat)


