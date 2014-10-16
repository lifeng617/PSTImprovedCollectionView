PSTImprovedCollectionView
=========================

This is an improved version of UICollectionView/PSTCollection:

(1) You can let the collection view preload 1 cell or one screen of cells that's not in screen yet, by calling

``` swift
    // in Swift
    if let flowLayout = collectionView.collectionViewLayout as? PSTCollectionViewFlowLayout {
        flowLayout.preloadMask = .Below  // or (.Above | .Below), or (.Left | .Right)
        flowLayout.preloadAmount = .OneScreen // this is optional, by default it preloads one cell
    }
```

(2) When you call collectionView.reloadData, dequeueReusableCellWithReuseIdentifier:indexPath: will try to provide you a cell with the original indexPath. So if you have a collection view loaded and just want to append more data or sections, you can simply call reloadData and in cellForItemAtIndexPath only re-render a cell when necessary (e.g. by comparing the model attached to the cell). This is useful because performBatchUpdates and insertItemsAtIndexPaths are much harder to coordinate when the table is more complex..

Thanks to Peter Steinberger and all the contributors of the original PSTCollectionView project ( steipete/PSTCollectionView)

## ARC

PSTCollectionView works with Xcode 4.5.2+ and ARC.

## Dependencies

PSTCollectionView needs the QuartzCore.framework.

## Interoperability

Another goal (at least super useful for debugging) is interoperability between UI/PST classes:

``` objective-c
UICollectionViewFlowLayout *flowLayout = [UICollectionViewFlowLayout new];
PSTCollectionView *collectionView = [[PSTCollectionView alloc] initWithFrame:self.view.bounds collectionViewLayout:(PSTCollectionViewFlowLayout *)flowLayout];
```

(*) Note that for some methods we can't use the _ underscore variants or we risk to get a false-positive on private API use. I've added some runtime hacks to dynamcially add block forwarders for those cases (mainly for UI/PST interoperability)


## License

PSTCollectionView is available under the MIT license. See the LICENSE file for more info.
