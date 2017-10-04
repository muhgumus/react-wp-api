Wordpress REST API (v2.0)
=========

Wordpress REST API (v2.0) component for JS (React, React native or pureJS)

## Installation

    `npm install react-wp-api` 


## Usage

    import _WP from 'react-wp-api';
    var WP = _WP('http://muhammedgumus.com')

    
Categories 
     
        WP.Categories().then((results) => {
            console.log(results)
            this.setState({ categories: results });
        })

       --  or --

        WP.Categories({id:2, search:'Tek'}).then((results) => {
            console.log(results)
            this.setState({ categories: results });
        })


Posts With Featured Images 

        WP.Posts().then((results) => {
            console.log(results)
            this.setState({ posts: results });

            results.forEach((item) => {
                WP.Media({ id: item.featured_media }).then((result) => {
                    let medias = this.state.medias;
                    medias['' + result.id] = {
                        thumbnail: result.media_details.sizes.thumbnail.source_url,
                        fullImage: result.media_details.sizes.full.source_url
                    }
                    this.setState({ medias });
                })
            }, this);

        })

       --  or -- 

    WP.Posts({id:2, category:4, search:'Ani'}).then((results) => {
            console.log(results)
            this.setState({ posts: results });
        })

       
Pages

        WP.Pages().then((results) => {
            console.log(results)
            this.setState({ pages: results });
        })

        -- or -- 
        
        WP.Pages({id:2, search:'Tek'}).then((results) => {
            console.log(results)
            this.setState({ pages: results });
        })

Media

        WP.Media().then((results) => {
            console.log(results)
            this.setState({ pages: results });
        })

        -- or -- 
        
        WP.Media({id:2, search:'Tek'}).then((results) => {
            console.log(results)
            this.setState({ pages: results });
        })

