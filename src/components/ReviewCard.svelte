<div class="ReviewCard-comp comp {customClass}">
    <div class="header">
        <img src="./assets/{user_name}.jpg" alt={user_name}>
        <div class="user-data">
            <h1>{user_name}</h1>
            <p>{part}</p>
        </div>
    </div>
    <p class="review">{review}</p>
</div>

<script>

export let user_name = ""
export let part = "Verified Buyer"
export let review = ""
export let customClass = 0
</script>

<style type="text/scss">
@import "../shared";
.ReviewCard-comp {
    display: flex;
    flex-direction: column;
    color:white;
    height: fit-content;
    background-color: hsl(300, 43%, 22%);
    gap: 30px;
    border-radius: 10px;
    .header {
        display: flex;
        align-items: center;
        img {
            border-radius: 100%;
        }
        .user-data {
            p , h1 {
                font-size: inherit;
            }
            p {
                color: hsl(333, 80%, 67%);
                margin-top: 10px;
            }            
        }
    }
    .review {
        line-height: 1.8;
        font-weight: 500;        
    }
}

@include media(">tablet") {
    .ReviewCard-comp {
        width: mathFromPcToTablet(430,230);
        padding: mathFromPcToTablet(40,20) mathFromPcToTablet(40,15);
        .header {
            gap: mathFromPcToTablet(25,15);
            font-size: mathFromPcToTablet(15,11);
            img {
                width: mathFromPcToTablet(45,40);
            }
        }
        .review {
            font-size: mathFromPcToTablet(15,11);
        }
    }
}
@include media("<=tablet") {
    .ReviewCard-comp .header {
        gap: 25px;
    } 
}
@include media("<=tablet",">phone") {
    .ReviewCard-comp {
        width: mathFromTabletToPhone(450,280);
        padding: mathFromTabletToPhone(40,30) 
                 mathFromTabletToPhone(30,20);
        .header {
            font-size: mathFromTabletToPhone(25,11);
            img {
                width: mathFromTabletToPhone(80,50);
            }
        }
        .review {
            font-size: mathFromTabletToPhone(14,11);
        }
    }  
}
@include media("<=phone") {
    .ReviewCard-comp {
        width: 280px;
        padding: 30px 20px;
        .header {
            font-size: 11px;
            img {
                width: 50px;
            }
        }
        .review {
            font-size: 11px;
        }
    }  
}
</style>