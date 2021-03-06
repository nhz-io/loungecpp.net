---
title: The indices trick
---

You have a tuple and you want to expand it as if it was a parameter pack. How do you solve that?

The indices trick basically amounts to tag dispatching to a structure that encodes all the indices.
Such a structure can be as simple as this:

```
template <std::size_t... Indices>
struct indices {};
```

Then we use a single tagged overload that uses type deduction to extract the parameters of `indices` as a pack:

```
template <Tuple, std::size_t... Indices>
std::array<int, std::tuple_size<Tuple>::value> f_them_all(Tuple&& t, indices<Indices...>) {
    return std::array<int, std::tuple_size<Tuple>::value> { { f(std::get<Indices>(std::forward<Tuple>(t)))... } }; 
}
```

Now all that's left is a way to build a pack of indices. Not that complicated.

```
template <std::size_t... Is>
struct indices {};

template <std::size_t N, std::size_t... Is>
struct build_indices
    : build_indices<N-1, N-1, Is...> {};

template <std::size_t... Is>
struct build_indices<0, Is...> : indices<Is...> {};

template <typename Tuple>
using IndicesFor = build_indices<std::tuple_size<Bare<Tuple>>::value>;
```

And the overload that builds the tag and dispatches:

```
template <typename Tuple>
std::array<int, std::tuple_size<Tuple>::value> f_them_all(Tuple&& t) {
    return f_them_all(std::forward<Tuple>(t), IndicesFor<Tuple> {});
}
```
