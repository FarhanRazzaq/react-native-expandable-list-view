![npm](https://img.shields.io/npm/v/react-native?color=%232fa90f&label=react-native&style=plastic)
![npm](https://img.shields.io/npm/dm/react-native-expandable-listview?style=plastic)

# About

This is a React-Native ExpandableListView component that you can freely modify its styles.

## Instalation

To install just input the following command:

```bash
npm i react-native-expandable-listview
```

or

```bash
yarn add react-native-expandable-listview
```

## Data Structure

```javascript

const CONTENT = [
  {
    isExpanded: false, // required, says wich one of the list has to expand or not
    categoryName: 'Item 1', // required, label of item expandable item
    subCategory: [ // required, array containing inner objects
        {
            id: 1, // required, of inner object
            name: 'Sub Cat 1', // required, label of inner object
        }, 
      {id: 3, name: 'Sub Cat 3'},
    ],
  },
  {
    isExpanded: false,
    categoryName: 'Item 8',
    subCategory: [{id: 22, name: 'Sub Cat 22',}],
  },
];

```

## Basic Usage

```javascript
//...

import ExpandableListView from 'react-native-expandable-listview';

const CONTENT = [
  {
    isExpanded: false,
    categoryName: 'Item 1',
    subCategory: [
      {id: 1, name: 'Sub Cat 1',},
      {id: 3, name: 'Sub Cat 3'},
    ],
  },
  {
    isExpanded: false,
    categoryName: 'Item 8',
    subCategory: [{id: 22, name: 'Sub Cat 22',}],
  },
];

export default class YourComponent extends Component {

    state = {
      listDataSource: CONTENT,
    }

    updateLayout = listDataSource => { //required
        this.setState({
            listDataSource,
        });
    };

    handleInnerClick = (innerIndex, headerItem) => { // required
        console.log(item.item.name);
    };

    render() {
    return (
        <ExpandableListView
          data={this.state.listDataSource} // required
          onInnerItemClick={this.handleInnerClick.bind(this)} // required
          onItemClick={this.updateLayout.bind(this)} //required
        />
    );
  }
}
```

## Advanced Usage

```javascript
//...

import ExpandableListView from 'react-native-expandable-listview';

const CONTENT = [
  {
    isExpanded: false,
    categoryName: 'Item 1',
    subCategory: [
      {id: 1, name: 'Sub Cat 1', innerCellHeight: 40,},
      {id: 3, name: 'Sub Cat 3'},
    ],
  },
  {
    cellHeight: 80, // if you want different height in specific Item of List
    isExpanded: false,
    categoryName: 'Item 2',
    subCategory: [
      {id: 4, name: 'Sub Cat 4', innerCellHeight: 60,}, // if you want different height  in specific inner Item of specific item of List
      {id: 5, name: 'Sub Cat 5',innerCellHeight: 40,},
    ],
  },
  {
    cellHeight: 40,
    isExpanded: false,
    categoryName: 'Item 7',
    subCategory: [{id: 20, name: 'Sub Cat 20', innerCellHeight: 40,}],
  },
  {
    cellHeight: 40,
    isExpanded: false,
    categoryName: 'Item 8',
    subCategory: [{id: 22, name: 'Sub Cat 22', innerCellHeight: 40,}],
  },
];

export default class YourComponent extends Component {

    state = {
      listDataSource: CONTENT,
    }

    updateLayout = listDataSource => {
        this.setState({
            listDataSource,
        });
    };

    handleInnerClick = (innerIndex, headerItem) => {
    console.log(item.item.name);
    };

    render(){
      return (
        <ExpandableListView
          // headerContainerStyle={{}} // add your styles to all item container of your list
          // headerLabelStyle={{}} // add your styles to all item text of your list
          // customChevron={{}} // your custom image to the indicator
          // chevronColor= "white" or "black" // select wich color of the default indicator
          // itemContainerStyle={{}} // add your styles to all inner item containers of your list
          // itemLabelStyle={{}} // add your styles to all inner item text of your list
          // headerImageIndicatorStyle={{}} // add your styles to the image indicator of your list
          data={this.state.listDataSource}
          onInnerItemClick={this.handleInnerClick.bind(this)}
          onItemClick={this.updateLayout.bind(this)}
        />
      )
    }
}
```

- All commented options above are optional.
- If you want to use the "customChevron" prop, provide a image path, for example:

```javascript
import chevron from '../assets/images/yourImage';
// ...
customChevron = {chevron};
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.