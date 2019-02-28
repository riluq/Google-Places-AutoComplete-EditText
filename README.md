<h1 align="center">Places AutoComplete EditText</h1>
<p align="center">
<a href="https://www.codacy.com/app/mukeshsolanki/Places-AutoComplete-EditText?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=mukeshsolanki/Places-AutoComplete-EditText&amp;utm_campaign=Badge_Grade"><img src="https://api.codacy.com/project/badge/Grade/e9f91e5cba1a4ebaaa51d532aa2afda8"/></a>
  <a href="https://jitpack.io/#mukeshsolanki/Places-AutoComplete-EditText"> <img src="https://jitpack.io/v/mukeshsolanki/Places-AutoComplete-EditText/month.svg" /></a>
  <a href="https://jitpack.io/#mukeshsolanki/Places-AutoComplete-EditText"> <img src="https://jitpack.io/v/mukeshsolanki/Places-AutoComplete-EditText.svg" /></a>
  <a href="https://circleci.com/gh/mukeshsolanki/Places-AutoComplete-EditText/tree/master"> <img src="https://circleci.com/gh/mukeshsolanki/Places-AutoComplete-EditText/tree/master.svg?style=shield" /></a>
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-blue.svg"/></a>
  <br /><br />
    A simple library that can connect your autocomplete edittext to Google's places api
</p>

<img src="https://raw.githubusercontent.com/mukeshsolanki/Places-AutoComplete-EditText/master/screenshots/ss1.png" width="270" height="480" /> &nbsp;&nbsp;
<img src="https://raw.githubusercontent.com/mukeshsolanki/Places-AutoComplete-EditTextmaster/screenshots/ss2.png" width="270" height="480" /> &nbsp;&nbsp;
<img src="https://raw.githubusercontent.com/mukeshsolanki/Places-AutoComplete-EditText/master/screenshots/ss3.png" width="270" height="480" /> &nbsp;&nbsp;

# Supporting Places AutoComplete EditText

Places AutoComplete EditText is an independent project with ongoing development and support made possible thanks to donations made by [these awesome backers](BACKERS.md#sponsors). If you'd like to join them, please consider:

- [Become a backer or sponsor on Patreon](https://www.patreon.com/mukeshsolanki).
- [One-time donation via PayPal](https://www.paypal.me/mukeshsolanki)

<a href="https://www.patreon.com/bePatron?c=935498" alt="Become a Patron"><img src="https://c5.patreon.com/external/logo/become_a_patron_button.png" /></a>

## How to integrate into your app?
Integrating the project is simple a refined all you need to do is follow the below steps

Step 1. Add the JitPack repository to your build file. Add it in your root build.gradle at the end of repositories:

```java
allprojects {
  repositories {
    ...
    maven { url "https://jitpack.io" }
  }
}
```
Step 2. Add the dependency
```java
dependencies {
        implementation 'com.github.mukeshsolanki:Places-AutoComplete-EditText:<latest-version>'
}
```

## How to use the library?
Okay seems like you integrated the library in your project but **how do you use it**? Well its really easy just add the following to your xml design

```xml
.....
 <AutoCompleteTextView
    android:id="@+id/autoCompleteEditText"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"/>
.....
```
To connect the AutoCompleteTextView to the places api create a PlaceApi object and attach it to the AutoCompleteTextView like-wise

```java
 val placesApi = PlaceAPI()
 placesApi.initialize("YOUR_API_KEY")
 autoCompleteEditText.setAdapter(PlacesAutoCompleteAdapter(this, placesApi))
```
That's pretty much it and your all wrapped up. You have successfully connected the Places Api to the AutoCompleteTextView.

## Getting details of place
To get the selected address simply set an ItemClickListener
```
autoCompleteEditText.onItemClickListener =
      AdapterView.OnItemClickListener { parent, _, position, _ ->
        val place = parent.getItemAtPosition(position) as Place
        autoCompleteEditText.setText(place.description)
      }
```
To get the details of the place selected you can set a listener to get the details
```
placesApi.fetchDetails("placeId", object : OnPlacesDetailsListener {
      override fun onError(errorMessage: String) {
        Toast.makeText(this@MainActivity, errorMessage, Toast.LENGTH_SHORT).show()
      }

      override fun onPlaceDetailsFetched(placeDetails: PlaceDetails) {
        //TODO do anything with placeDetails object
      }
    })
```

## Author
Maintained by [Mukesh Solanki](https://www.github.com/mukeshsolanki)

## Contribution
[![GitHub contributors](https://img.shields.io/github/contributors/mukeshsolanki/Places-AutoComplete-EditText.svg)](https://github.com/mukeshsolanki/Places-AutoComplete-EditText/graphs/contributors)

* Bug reports and pull requests are welcome.
* Make sure you use [square/java-code-styles](https://github.com/square/java-code-styles) to format your code.

## License
```
MIT License

Copyright (c) 2019 Mukesh Solanki

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
