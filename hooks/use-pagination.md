# React Hooks

Useful hooks for react JS, super easy to use and can handel all the major user cases.
##### Based on the React hooks and reactive programing.
#### No extra dependencies pure react js code & lightweight.

## Features
1. Useful hooks for react js.
2. Open source Free to use.

## Installation
```sh
npm install @surinderlohat/react-hooks
or
yarn add @surinderlohat/react-hooks
```
## API Documentation
| Functions/Props |  DESCRIPTION | Type
| ------ | ------ | ----- |
| allowBack | Enable/Disable back navigation | boolean
| allowNext | Enable/Disable next navigation | boolean
| isLoading | Show loader when making api callls | boolean
| showLoader | Make isLoading =true | Function
| hideLoader | Make isLoading =false | Function
| setPagingData | used to set pagination data i.e array of items pageSize, pageNumber and total number of records | Function
| setPageSize | Number of records needs to get with each request i.e 10 ,20,30 | Function
| goToNextPage | Next page navigation | Function
| goToPreviousPage | Previous page navigation | Function
| goToFirstPage | Goto first page from any page | Function
| gotoSpecificPage | Goto any specific page  i.e pagination.gotoSpecificPage(5) goto page number 5 if available | Function 
| goToLastPage | Goto last page | Function

## How to use :
```sh
import { FC } from 'react';
import { Box, Button } from '@mui/material';

// Import usePagination hook
import { usePagination, IPageRequest } from '@surinderlohat/react-hooks';

const PaginationHook: FC = () => {
  // pageSize 10,20,30 etc
  // callback when pagination change
  const pagination = usePagination(20, pagination => fetchDataFromApi(pagination));

  // Mocking the APi Call
  const fetchDataFromApi = (response: IPageRequest) => {
    pagination.showLoader();
    // See response here from API
    console.log(response);

    // Mocking API Call
    setTimeout(() => {
      pagination.hideLoader();
    }, 5000);
  };

  return (
    <Box sx={{ display: 'flex', justifyContent: 'center' }}>
      <Box>
        <Button disabled={!pagination.allowBack} onClick={() => pagination.goToPreviousPage()}>
          Back
        </Button>
        <Button disabled={!pagination.allowNext} onClick={() => pagination.goToNextPage()}>
          Next
        </Button>
        <Box>
          <Button disabled={pagination.pageNumber <= 1} onClick={() => pagination.goToFirstPage()}>
            Goto First Page
          </Button>
          {Array.from(Array(10).keys()).map(pageNumber => (
            <Button
              key={pageNumber}
              onClick={() => pagination.gotoSpecificPage(pageNumber + 1)}
              style={{
                color: pageNumber + 1 === pagination.pageNumber ? 'red' : 'blue',
              }}
            >
              {pageNumber + 1}
            </Button>
          ))}
          <Button disabled={!pagination.isLastPage} onClick={() => pagination.goToFirstPage()}>
            Goto Last Page
          </Button>
        </Box>
        {pagination.isLoading && 'Loading Data From API'}
      </Box>
    </Box>
  );
};

export default PaginationHook;


```

## License
MIT **Free Software!**
