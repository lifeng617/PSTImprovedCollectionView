PSTCollectionView
=================

The initial purpose of PSTCollectionView was to bring UICollectionView to iOS 4 and 5, but as right now most apps don't support iOS 5 any more, the main focus of this fork is to add a cell preload feature to collection view.

Thanks to Peter Steinberger and all the contributors of the original PSTCollectionView project ( steipete/PSTCollectionView)

## Animations

Thanks to Sergey Gavrilyuk ([@octogavrix](https://twitter.com/octogavrix)), animations are supported. It's not perfect yet (see LineExample), but it's a great start.

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

## Creator

[Peter Steinberger](http://petersteinberger.com) ([@steipete](https://twitter.com/steipete))
and lots of others! See [Contributors](https://github.com/steipete/PSTCollectionView/graphs/contributors) for a graph. Thanks everyone!

## License

PSTCollectionView is available under the MIT license. See the LICENSE file for more info.
