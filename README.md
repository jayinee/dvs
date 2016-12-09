<!-- fullCalendar 2.2.5 -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.11.2/moment.min.js"></script>
<script src="../plugins/fullcalendar/fullcalendar.min.js"></script>

<link rel="stylesheet" href="../plugins/fullcalendar/fullcalendar.min.css">
<link rel="stylesheet" href="../plugins/fullcalendar/fullcalendar.print.css" media="print">
<style>
    .modal-content {
        box-shadow: none;
        border: none;
    }

    .data-list li .title span {
        display: inline-block;
        padding: 0 10px 2px 15px;
        background: #ffffff;
        margin-bottom: -2px;
        margin-left: -15px;
    }
</style>
<section class="content">
    <div class="row">
        <div class="col-md-3">
            <div class="box-body">
                <div class="btn-group" style="width: 100%; margin-bottom: 10px;">
                </div>
            </div>
        </div>
        <div class="col-md-12">
            <div class="box box-primary">
                <div class="box-body no-padding">
                    <!-- THE CALENDAR -->
                    <div id="calendar">

                    </div>
                </div>
                <!-- /.box-body -->
            </div>
            <!-- /. box -->
        </div>
    </div>
    
    <div class="modal fade" id="myModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>
                    <h4 class="modal-title" id="myModalLabel">Booking info</h4>
                </div>
                <div class="modal-body">
                    <div class="row">
                        <div class="col-lg-6 col-sm-12">
                            <div class="form-group">
                                <div class="info-box bg-blue">
                                        <span class="info-box-icon"><i class="fa fa-calendar"></i></span>
                                        <div class="info-box-content">
                                            <span class="info-box-number">01-11-2016</span>
                                            <span class="info-box-text">14:00 - 15:00</span>
                                            <span class="info-box-text"><i class="fa fa-fw fa-hourglass"></i>1 hour</span>
                                        </div>
                                        <!-- /.info-box-content -->
                                    </div>
                                <div class="col-lg-6 col-sm-12">
                                    <div class="form-group">
                                        <div>
                                            <ul>
                                                <li>
                                                    <span><i class="fa fa-user"></i>Client names</span>
                                                    <span>antriksh</span>
                                                </li>
                                            </ul>
                                        </div>
                                        <label>Company Name ........................ BizTech Solution</label>
                                    </div>
                                    <div class="form-group">
                                        <label>Client Name ......................... Divyesh Panchal</label>
                                    </div>
                                    <div class="form-group">
                                        <label>Email</label>
                                    </div>
                                    <div class="form-group">
                                        <label>Contact no</label>
                                    </div>
                                </div>
                                </div>
          
                            </div>
                      </div>
                   </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
                        <button type="button" class="btn btn-primary">View Detail</button>
                    </div>
                </div>
                
          </div>
            </div>
                
</section>
<script>
    $(function () {

        /* initialize the external events
         -----------------------------------------------------------------*/
        function ini_events(ele) {
            ele.each(function () {

                // create an Event Object (http://arshaw.com/fullcalendar/docs/event_data/Event_Object/)
                // it doesn't need to have a start or end
                var eventObject = {
                    title: $.trim($(this).text()) // use the element's text as the event title
                };

                // store the Event Object in the DOM element so we can get to it later
                $(this).data('eventObject', eventObject);

                // make the event draggable using jQuery UI
                $(this).draggable({
                    zIndex: 1070,
                    revert: true, // will cause the event to go back to its
                    revertDuration: 0  //  original position after the drag
                });

            });
        }

        ini_events($('#external-events div.external-event'));

        /* initialize the calendar
         -----------------------------------------------------------------*/
        //Date for the calendar events (dummy data)
        var date = new Date();
        var d = date.getDate(),
            m = date.getMonth(),
            y = date.getFullYear();



        //$('#calendar').fullCalendar({
        //    header: {
        //        left: 'prev,next today',
        //        center: 'title',
        //        right: 'month,agendaWeek,agendaDay'
        //    },
        //    buttonText: {
        //        today: 'today',
        //        month: 'month',
        //        week: 'week',
        //        day: 'day'
        //    },


        //        dayClick: function (date, jsEvent, view) {

        //            alert('Clicked on: ' + date.format());



        // change the day's background color just for fun
        //        $(this).css('background-color', 'skyblue');

        //    }
        //});
        $('#calendar').fullCalendar({
            header: {
                left: 'prev,next today',
                center: 'title',
                right: 'month,agendaWeek,agendaDay'
            },
            buttonText: {
                today: 'today',
                month: 'month',
                week: 'week',
                day: 'day'
            },
            //Random default events
            events: [
              {
                  title: '14:00-15:00 biztech solution',
                  start: new Date(y, m, 1),
                  backgroundColor: "#f39c12", //yellow
                  borderColor: "#f56954" //red
              },
              {
                  title: '11:00-15:00 Appointment with IT engineer',
                  start: new Date(y, m, d - 5),
                  end: new Date(y, m, d - 2),
                  backgroundColor: "#f39c12", //yellow
                  borderColor: "#f39c12" //yellow
              },
              {
                  title: '11:00-15:00 Appointment',
                  start: new Date(y, m, d, 10, 30),
                  allDay: false,
                  backgroundColor: "#0073b7", //Blue
                  borderColor: "#0073b7" //Blue
              },
              {
                  title: '15:00-16-00 Lunch',
                  start: new Date(y, m, d, 12, 0),
                  end: new Date(y, m, d, 14, 0),
                  allDay: false,
                  backgroundColor: "#00c0ef", //Info (aqua)
                  borderColor: "#00c0ef" //Info (aqua)
              },

              //{
              //    title: 'Click for Google',
              //    start: new Date(y, m, 28),
              //    end: new Date(y, m, 29),

              //    url: 'http://google.com/',
              //    backgroundColor: "#3c8dbc", //Primary (light-blue)
              //    borderColor: "#3c8dbc" //Primary (light-blue)
              //}
            ],
            editable: true,
            droppable: true, // this allows things to be dropped onto the calendar !!!
            drop: function (date, allDay) { // this function is called when something is dropped

                // retrieve the dropped element's stored Event Object
                var originalEventObject = $(this).data('eventObject');

                // we need to copy it, so that multiple events don't have a reference to the same object
                var copiedEventObject = $.extend({}, originalEventObject);

                // assign it the date that was reported
                copiedEventObject.start = date;
                copiedEventObject.allDay = allDay;
                copiedEventObject.backgroundColor = $(this).css("background-color");
                copiedEventObject.borderColor = $(this).css("border-color");

                // render the event on the calendar
                // the last `true` argument determines if the event "sticks" (http://arshaw.com/fullcalendar/docs/event_rendering/renderEvent/)
                $('#calendar').fullCalendar('renderEvent', copiedEventObject, true);

                // is the "remove after drop" checkbox checked?
                if ($('#drop-remove').is(':checked')) {
                    // if so, remove the element from the "Draggable Events" list
                    $(this).remove();
                }

            },

            eventClick: function (calEvent, jsEvent, view) {

                //alert('Event: ' + calEvent.title);
                //alert('Coordinates: ' + jsEvent.pageX + ',' + jsEvent.pageY);
                //alert('View: ' + view.name);
                $('#myModal').modal('show');
                // $('#myModal').modal('hide');

                // change the border color just for fun
                $(this).css('border-color', 'red');

            }
        });

        /* ADDING EVENTS */
        var currColor = "#3c8dbc"; //Red by default
        //Color chooser button
        var colorChooser = $("#color-chooser-btn");
        $("#color-chooser > li > a").click(function (e) {
            e.preventDefault();
            //Save color
            currColor = $(this).css("color");
            //Add color effect to button
            $('#add-new-event').css({ "background-color": currColor, "border-color": currColor });
        });
        $("#add-new-event").click(function (e) {
            e.preventDefault();
            //Get value and make sure it is not null
            var val = $("#new-event").val();
            if (val.length == 0) {
                return;
            }

            //Create events
            var event = $("<div />");
            event.css({ "background-color": currColor, "border-color": currColor, "color": "#fff" }).addClass("external-event");
            event.html(val);
            $('#external-events').prepend(event);

            //Add draggable funtionality
            ini_events(event);

            //Remove event from text input
            $("#new-event").val("");
        });
    });
</script>
